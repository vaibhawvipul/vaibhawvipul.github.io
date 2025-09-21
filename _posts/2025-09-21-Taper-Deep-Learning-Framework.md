---
layout: post
title: 'Taper: Hacking a Deep Learning Framework from Scratch'
date: 2025-09-21
author: "Vipul Vaibhaw"
---

# taper
A small neural network library in Rust built to understand how things actually work.

taper implements the basic building blocks: tensors, automatic differentiation, and common operations. The goal isn't to compete with existing frameworks - it's to learn by building from scratch.

What's inside:
- Tensors are Vec<f32> with shape metadata
- Tape-based autograd that tracks operations for backprop
- Basic optimizations: SIMD for element-wise ops, BLAS for matrix multiply
- Standard convolution via im2col + GEMM
- Common layers: Linear, Conv2d, pooling, activations

Performance (M1 Mac, CPU only):
- MLP on MNIST: 0.22s/epoch (PyTorch baseline: 1.5s/epoch)
- CNN on MNIST: 22s/epoch for batch size 256

The MLP performance comes from using Accelerate BLAS and avoiding Python overhead.

The CNN implementation is straightforward but unoptimized - there's room for improvement with better kernel fusion and memory layouts.

----

This is a learning project not a prod framework yet.

If you want to understand what happens when you call .conv2d() or .backward(), read the source and modify it.

That's the point.
Check it out on [GitHub](https://github.com/vaibhawvipul/taper).
