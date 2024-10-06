---
layout: post
title: Exploring query processing paradigms - Compiled and Vectorized
author: "Vipul Vaibhaw"
---

*Note: I use AI models to help with writing. Now, this is more like notes for me so you will find stuff copied directly from various places. If you spot any mistakes, feel free to correct me!*

I was reading this [paper](https://www.vldb.org/pvldb/vol11/p2209-kersten.pdf) on query processing paradigms and found it quite interesting.

This paper compares two query processing paradigms, vectorization and data-centric code generation, by implementing both within the same test system.

Vectorization excels at hiding cache miss latency, while data-centric compilation requires fewer CPU instructions, making it better for cache-resident workloads. The study also examines SIMD, multi-core parallelization, and hardware architectures to offer a comprehensive performance analysis.

---

# Compiled and Vectorized Queries

Many query engines implement relational operators using a volcano-style iteration, where each operator processes one tuple at a time. Though flexible, this approach is inefficient on modern CPUs, especially for in-memory database management systems (DBMSs), as it was originally designed for disk-bound systems.

Most modern query engines therfore either use vectorization(like datafusion) or data-centric code generation(like Apache Spark).

Similar to Volcano-style iteration model, vectorization uses pull-based iteration, but processes multiple tuples at once.

In contrast, Data-centric code generation uses a push-based iteration model, where operators generate code for a query through produce/consume calls during a depth-first traversal of the query plan. This process creates specialized code for the query's data types, fusing operators into a single loop, which is then compiled into efficient machine code (e.g., using LLVM).

While both models are efficient and eliminate traditional engine overhead, they differ conceptually: vectorization uses a pull model (root-to-leaf traversal), processes data in vectors, and interprets the query, whereas data-centric code generation follows a push model (leaf-to-root traversal), processes data one tuple at a time, and compiles the query upfront.

The differences of the two models are fundamental and determine the organization of the DBMS’s execution engine source code
and its performance characteristics. Because changing the model requires rewriting large parts of the source code, DBMS designers must decide early on which model to use.

The fundamental differences between the two models influence the structure of the DBMS execution engine's source code and its performance characteristics. Since switching models necessitates extensive code rewrites, DBMS designers must make this decision early in the design process.

---

# Vectorized vd Compiled Queries

They key idea behind vectorized query processing is to process multiple tuples at once, rather than one at a time.

Data-centric compilation generates low-level code for a SQL query that fuses all adjacent non-blocking operators into a single loop.

## Vectorized Hash Join and Group By

### Vectorized Hash Join

Build Phase
- Load first input into hash table in row format for better cache locality.


Probe Phase:
- For each tuple from the second input, the hash table is probed. A vectorized hash join uses the probeHash expression to create hashes from the probe keys.
- The keys are hashed by invoking one primitive per key column (for composite keys) and are written into an output vector.
- The resulting hash vector is used to generate candidate match locations in the hash table, which are then checked for key equality using the cmpKey expression.


Equality Check:
- For composite join keys, the equality check involves multiple primitives (one per key column).
- Matching tuples are added to a list, and overflow entries (if any) are processed as new candidates for further iterations.

Gathering Results:
- Once matches are found, the buildGather function is used to move the data from the hash table into buffers for the next operator.

### Vectorized Group By

Hash Table Setup:
- The group-by operator uses a hash table containing group keys and aggregates. The hash table is populated using the same method as in the hash join.

Handling Group-less Tuples:
- If a tuple's group is not found in the hash table, it is added. However, to avoid adding duplicate groups for group-less tuples, tuples are partitioned by equal keys (proceeding key component by key component for composite keys).

Aggregation:
- Once the groups are identified, aggregation primitives are executed for all inbound tuples.

### Challenges in Vectorization:
- Vectorization imposes constraints requiring different implementations for the same algorithm compared to non-vectorized systems, particularly affecting data access patterns.

### Performance:
- While join operations lead to more independent data access, the aggregation phase incurs extra work in vectorized form due to its additional complexities.

---

# Summary

Surprisingly, the performance of vectorized and data-centric compiled query execution is quite similar in OLAP workloads. Key findings include:

- **Computation**: Data-centric compiled code excels in computationally-intensive queries, reducing instruction count by keeping data in registers.
- **Parallel Data Access**: Vectorized execution performs slightly better in memory-bound queries by generating parallel cache misses, benefiting large hash-table lookups.
- **SIMD Utilization**: Though vectorized execution theoretically benefits more from SIMD, the practical advantage is small due to memory access being the bottleneck.
- **Parallelization**: Both approaches scale well on multi-core CPUs using morsel-driven parallelism.
- **Hardware**: The performance comparison holds across various platforms (Intel Skylake, Knights Landing, AMD Ryzen) with neither vectorization nor compilation having a clear edge.

Additional factors:
- **Data-Centric Engines**: Excel in OLTP for fast stored procedures and language integration.
- **Vectorized Engines**: Have faster compile times (pre-compiled primitives), better profiling (runtime attributed to primitives), and can adapt execution mid-query.