# Matrix Product Verifier: Deterministic Verification and Correction Algorithms

## 💡 Short Description

This repository contains the **implementation and empirical evaluation** of deterministic algorithms for verifying and correcting erroneous matrix products.

The goal is to investigate methods for scenarios where **computational integrity** (e.g., in outsourced computations) must be guaranteed, and to benchmark these methods against common probabilistic procedures (Freivalds) and optimized hardware implementations (PyTorch).

The implementation is based on the formal frameworks developed by Künnemann and Gąsieniec et al.

## 🔑 Core Functionality and Methodology

* **Verification:** Implementation of Künnemann's deterministic verification algorithm (runtime $\tilde{\mathcal{O}}(n^2+tn)$).
* **Correction:** Implementation of the Gąsieniec et al. algorithm for error correction (runtime $\tilde{\mathcal{O}}(tn^2)$).
* **Performance Analysis:** Detailed **benchmarking in Python** to determine the practical runtime on **synthetic and real-world matrices** (SuiteSparse Collection).
* **Key Findings:** Empirical confirmation of the theoretical complexity and identification of **Fast Multipoint Evaluation (FME)** as the dominant cost factor (up to 97% of runtime).

## 🛠️ Technologies

* **Language:** Python
* **Libraries:** NumPy, PyTorch (`torch.matmul` for baseline comparisons), FLINT (via Python Bindings for number-theoretic computations).
* **Tools:** Matplotlib (for results visualization)
