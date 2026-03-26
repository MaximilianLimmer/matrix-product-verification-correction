# Matrix Product Verifier: Deterministic Verification and Correction

### The Objective
In high-performance computing and outsourced computation, verifying the integrity of a matrix product $C = A \times B$ is critical. While probabilistic methods like Freivalds’ algorithm are common, they carry a non-zero error probability. 

This repository implements and benchmarks **deterministic, output-sensitive algorithms** that guarantee 100% computational integrity, specifically optimized for scenarios where the number of errors ($t$) is small relative to the matrix dimension ($n$).

### Methodology & Algorithmic Moat

The implementation follows the formal frameworks of **Künnemann** and **Gąsieniec et al.**, focusing on minimizing the overhead of verification in sparse-error settings.

#### 1. Deterministic Verification (Künnemann)
* **Complexity:** $\tilde{\mathcal{O}}(n^2 + tn)$
* **Logic:** Instead of random sampling, the algorithm uses a deterministic approach to identify if $A \times B \neq C$.
* * **Optimization:** Leverages **Fast Multipoint Evaluation (FME)**. My analysis identified FME as the primary bottleneck, accounting for up to 97% of total runtime, which led to specialized number-theoretic optimizations.

#### 2. Error Correction (Gąsieniec et al.)
* **Complexity:** $\tilde{\mathcal{O}}(tn^2)$
* **Logic:** An output-sensitive algorithm that not only detects but **corrects** $t$ erroneous entries without re-computing the entire product.




#### 3. Empirical Benchmarking
I benchmarked these deterministic methods against:
* **Probabilistic Baselines:** Freivalds’ Algorithm.
* **Hardware Baselines:** Highly optimized PyTorch implementations.
* **Datasets:** Synthetic stress tests and real-world sparse matrices from the **SuiteSparse Matrix Collection**.

---

### Key Engineering Insights
* **Complexity Validation:** Empirically confirmed that for $t \ll n$, deterministic verification outperforms full re-computation, particularly in sparse settings where $\mathcal{O}(n^{\omega})$ is prohibitive.
* **Bottleneck Analysis:** Identified that the constant factors in FME are the primary hurdle for practical adoption. This led to an investigation of FLINT-based number-theoretic optimizations to reduce the overhead of polynomial evaluations.

---

### Technical Stack
* **Core:** Python, NumPy.
* **Optimization:** **FLINT** (Fast Library for Number Theory) via Python bindings for high-speed modular arithmetic and polynomial operations.
* **Baseline Comparison:** PyTorch (for GPU-accelerated GEMM comparison).
* **Visualization:** Matplotlib for profiling and complexity curve analysis.

---
