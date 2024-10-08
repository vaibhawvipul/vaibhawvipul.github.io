---
layout: post
title: Thoughts about Datafusion - part 1
author: "Vipul Vaibhaw"
---

I have been involved with [Datafusion](https://github.com/apache/datafusion) and related projects for a while now. The following are some of my thoughts about Datafusion and its ecosystem. This is the first part of a series of posts I plan to write about Datafusion project.

*Note: These are my personal thoughts and opinions and do not represent the views of any organization I am associated with. Also, I can be wrong in my understanding of the project and its ecosystem. Please feel free to correct me if you find any mistakes. Also, the views may change later in the future.*

## What is Datafusion?

Apache Datafusion is a Rust-native query engine that is designed to be arrow-native and support multiple backends. It is volcano-style pull-based vectorized query engine.

## Why I am excited about Datafusion?

I am excited about Datafusion because of the following reasons:
- It is aiming to be LLVM for data processing.
- It is written in Rust, which is a modern systems programming language that gives us more control over JVM-based engines.
- It is designed to be arrow-native, which means it can leverage the Arrow ecosystem.
- etc.

## What would I improve in Datafusion?

I would like to explore the following areas as potential improvements in Datafusion:

- **IO Uring Support:** - As of now, Datafusion uses the `tokio` runtime as a scheduler. I would like to explore the possibility of using `io_uring` based scheduler for better performance. `io_uring` is a modern asynchronous I/O interface that is available in Linux kernel.

- **Acceleration of Datafusion using GPUs:** - I would like to explore the possibility of accelerating Datafusion using GPUs. Nvidia-Rapids for Datafusion could be a potential project.

- **Integration with Pytorch:** - Allowing Datafusion to run Pytorch models natively could be a potential project. Machine learning udfs could be exciting.