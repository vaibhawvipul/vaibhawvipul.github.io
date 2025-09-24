---
layout: post
title: "Taper: A Minimal Deep Learning Core"
date: 2025-09-24
author: "Vipul Vaibhaw"
---

# Taper: Building a Neural Network Library in Rust

Taper is a small neural network library written in Rust. [Taper - GitHub Repo](https://github.com/vaibhawvipul/taper)

It’s not production-ready, and it’s not trying to replace existing frameworks. The goal was to learn: how automatic differentiation works, how to write fast kernels, and how low-level choices affect performance on CPU.

Performance (M4 Mac, CPU only):
- MLP on MNIST: ~0.22s/epoch (PyTorch baseline: 1.5s/epoch)
- CNN on MNIST: ~12s/epoch for batch size 256 (PyTorch baseline: 120s/epoch)

---

## Tape-Based Autograd

Taper uses a tape to record operations during the forward pass. Each op pushes a closure that knows how to compute gradients. Backprop just walks the tape in reverse:

```rust
Tape::push_binary_op(self, other, &output, move || {
    if let Some(gout) = out.grad.read().unwrap().as_ref() {
        accumulate_grad(&a, gout);
        accumulate_grad(&b, gout);
    }
});
```

This keeps autograd simple and fully dynamic.

---

## Matrix Multiplication and BLAS

Most of training time is matrix multiplication.

Taper uses two paths:
- BLAS when available (Apple Accelerate, Intel MKL, OpenBLAS):

```rust
cblas_sgemm(
    CblasRowMajor, CblasNoTrans, CblasNoTrans,
    m, n, k,
    1.0, a.as_ptr(), lda,
    b.as_ptr(), ldb,
    0.0, c.as_mut_ptr(), ldc
);
```
- Fallback Rust GEMM: cache-blocked SGEMM with SIMD micro-kernels.

This hybrid design keeps it portable and fast.

---

## SIMD Kernels

Elementwise ops don’t benefit from BLAS, so Taper uses explicit SIMD:

```rust
#[target_feature(enable = "avx")]
unsafe fn add_f32_avx(a: &[f32], b: &[f32], out: &mut [f32]) {
    let chunks = a.len() / 8;
    for i in 0..chunks {
        let va = _mm256_loadu_ps(a.as_ptr().add(i * 8));
        let vb = _mm256_loadu_ps(b.as_ptr().add(i * 8));
        let res = _mm256_add_ps(va, vb);
        _mm256_storeu_ps(out.as_mut_ptr().add(i * 8), res);
    }
}
```

Supported backends: AVX2 (x86), NEON (ARM), scalar fallback.

---

## Convolution Kernels

Convolution uses different strategies depending on the case:

- 3×3 direct: unrolled loops (9 multiply–adds directly), no im2col.
- 1×1: just a matmul.
- General: im2col -> GEMM.

This avoids overhead for common cases.

Note - Im2col (Image to Column) is a data transformation technique used in convolutional neural networks (CNNs) to convert convolution operations into General Matrix to Matrix Multiplication (GEMM) (or GEMM) operations.

---

## Operation Fusion

Common patterns are fused to reduce memory traffic:

```rust
pub fn conv2d_relu(&self, weight: &Tensor, bias: Option<&Tensor>) -> Tensor {
    let conv_out = self.conv2d(weight, bias, (1,1), (0,0), (1,1));
    conv_out.relu_inplace()
}
```

---

## Parallelism and Memory Layout

- Batch and channel parallelism via Rayon:
```rust
output.par_chunks_mut(h_out * w_out)
    .enumerate()
    .for_each(|(idx, out_spatial)| { /* ... */ });
```

- Cache-blocked transpose and matmul to stay inside L1/L2 cache.

---

## Minimal Scope

The library includes:
- Tensor ops with autograd
- Linear, Conv2D, Pooling, ReLU/Sigmoid
- SGD and Adam
- Simple training loops (MNIST examples)
- About 3k lines of code in total.

---

## Lessons Learned

- BLAS level 3 supercharges GEMM.
- SIMD for elementwise ops.
- Memory bandwidth is the bottleneck; fusing ops and blocking is critical.
- Rust makes parallelism safer to write.
- A minimal design is easier to optimize.

Try It -
```bash
git clone https://github.com/vaibhawvipul/taper.git
cd taper
cargo run --release --features blas-accelerate --example train_mnist
cargo run --release --features blas-accelerate --example train_mnist_cnn
```

---

Taper is a compact experiment in deep learning internals. It shows how far careful engineering can take you, even on CPU, and makes the tradeoffs explicit in code that’s small enough to read in a weekend.

---

reach out on [x](https://x.com/vaibhaw_vipul) or [github](https://github.com/vaibhawvipul) or [email](vaibhaw.vipul@gmail.com) for more.
