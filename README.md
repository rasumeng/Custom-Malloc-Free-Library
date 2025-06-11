# Custom-Malloc-Free-Library
A deep dive into heap memory management: Building malloc(), free(), calloc(), and realloc() from scratch.
# 📘 Project Overview
This project is a handcrafted memory management library written in C that implements the core logic behind malloc() and free(), along with advanced allocation strategies. It mimics system-level memory allocation and management while exposing internal metrics like block reuse, splitting, coalescing, and heap growth.

I created this to explore the internals of dynamic memory allocation and understand the performance trade-offs between different fit strategies. This project became a mini deep-dive into operating systems, memory fragmentation, and data structure efficiency.

# ✨ Features
## ✅ Custom implementations of:

malloc()

free()

calloc()

realloc()

## 🧩 Four fit strategies:

First Fit

Best Fit

Next Fit

Worst Fit

## ⚙️ Memory block handling:

Block splitting (if too large)

Block coalescing (merge adjacent free blocks)

## 📊 Built-in performance counters:

Total mallocs/frees

Reuses vs. heap growth

Splits, coalesces, heap size

## 📈 Benchmark suite:

Performance vs. system malloc()

Fragmentation analysis

Heap growth comparison

# 🛠️ Building & Running
To compile:

```
make
```
To run a test with a specific fit strategy:
```

env LD_PRELOAD=lib/libmalloc-ff.so tests/ffnf
```
Available allocator libraries:

libmalloc-ff.so – First Fit

libmalloc-bf.so – Best Fit

libmalloc-nf.so – Next Fit

libmalloc-wf.so – Worst Fit

Eight test programs are located in the tests/ directory for validating allocator behavior.

# 📉 Benchmarking and Evaluation
I developed a benchmarking suite that evaluates:

Execution time

Number of splits and heap growths

Heap fragmentation

Maximum heap size

The results were compared across all four custom allocators and the system malloc(). The system allocator was only benchmarked for performance, as internals are inaccessible.

## 🧪 Sample Statistics Output (Generated on Exit)
```
mallocs:     8
frees:       8
reuses:      1
grows:       5
splits:      1
coalesces:   1
blocks:      5
requested:   7298
max heap:    4096
```
Note: These values are generated and updated dynamically by each allocator and are unique per run.

# 📝 What I Learned
How memory is managed at the OS level

Designing linked free-list allocators

Trade-offs between allocation strategies

How fragmentation and reuse impact performance

System programming techniques (e.g., sbrk(), LD_PRELOAD, dlopen debugging)
