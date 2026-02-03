# Quantum Foundations 🧠

This directory contains the fundamental mathematical frameworks and physical principles required for Quantum Machine Learning. It serves as the bedrock for understanding advanced algorithms.

## 📂 Module Index

| Sequence | Notebook File | Key Concepts |
| :--- | :--- | :--- |
| **01** | `01_Hello_Entanglement.ipynb` | **Entanglement**, Bell States, Tensor Products ($\otimes$), Measurement Collapse. |
| **02** | `02_Single_Qubit_Gates.ipynb` | **Linear Algebra**, Pauli-X Gate, Hadamard Gate, Superposition, Phase vs. Probability. |

---

## 📚 Theoretical Summary

### Module 01: Entanglement (The "Hello World" of QML)
- **Concept:** Quantum entanglement is a phenomenon where two particles become linked, such that the state of one cannot be described independently of the other.
- **Key State (Bell State):**
  $$|\Phi^+\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}}$$
- **Observation:** Measuring the first qubit immediately determines the outcome of the second qubit, regardless of distance.

### Module 02: Single Qubit Gates
- **The Pauli-X Gate (NOT Gate):** Rotates the state by $\pi$ around the X-axis (Bit Flip).
  $$X = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}, \quad X|0\rangle = |1\rangle$$
- **The Hadamard Gate (H):** Creates Superposition from basis states.
  $$H = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}$$
  $$H|0\rangle = |+\rangle = \frac{|0\rangle + |1\rangle}{\sqrt{2}}$$
- **Phase:** We demonstrated that $H|1\rangle = |-\rangle$. While $|+\rangle$ and $|-\rangle$ have the same measurement probabilities ($50/50$), they differ in **phase**, which is crucial for interference algorithms.