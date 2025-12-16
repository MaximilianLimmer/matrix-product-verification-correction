This repository contains the **implementation and empirical evaluation** of deterministic algorithms for verifying and correcting erroneous matrix products.

[cite_start]The goal is to study methods for scenarios requiring **computational integrity** (e.g., in outsourced computation) [cite: 65, 68, 71] [cite_start]and to benchmark them against common probabilistic approaches (Freivalds) and optimized hardware implementations (PyTorch)[cite: 65, 68, 71].

The implementation is based on the formal frameworks of Künnemann [Kün18] and Gąsieniec et al. [cite_start][Gąs+17][cite: 109, 113, 136].

## 🔑 Core Functionality and Methodology

* [cite_start]**Verification:** Implementation of Künnemann's deterministic verification algorithm (runtime $\tilde{\mathcal{O}}(n^2+tn)$)[cite: 109, 219, 330].
* [cite_start]**Correction:** Implementation of the Gąsieniec et al. algorithm for error correction (runtime $\tilde{\mathcal{O}}(tn^2)$)[cite: 113, 219].
* [cite_start]**Performance Analysis:** Detailed **benchmarking in Python** to determine the practical runtime on **synthetic and real-world matrices** (SuiteSparse Collection)[cite: 28, 400, 412].
* [cite_start]**Key Findings:** Empirical confirmation of the theoretical complexity and identification of **Fast Multipoint Evaluation (FME)** as the dominant cost driver (up to 97% of runtime)[cite: 46, 489, 499].

## 🛠️ Technologies

* **Language:** Python
* [cite_start]**Libraries:** NumPy, PyTorch (`torch.matmul` for baseline comparisons), FLINT (via Python Bindings for number-theoretic computations)[cite: 397, 398, 505].
* [cite_start]**Tools:** Matplotlib (for result visualization)[cite: 49, 443].
