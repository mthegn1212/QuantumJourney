# Quantum Foundations 🧠

This directory contains the fundamental mathematical frameworks and physical principles required for Quantum Machine Learning. It serves as the bedrock for understanding advanced algorithms.

## 📂 Module Index

| Sequence | Notebook File | Key Concepts |
| :--- | :--- | :--- |
| **01** | `01_Hello_Entanglement.ipynb` | **Entanglement** (Day 3), Tensor Products ($\otimes$), CNOT Gate, Bell States. |
| **02** | `02_Single_Qubit_Gates.ipynb` | **Single Qubit Gates** (Day 2), Linear Algebra, Superposition, Bloch Sphere. |

---

## 📚 Theoretical Deep Dive

### Module 01: Multi-Qubit Systems & Entanglement (Day 3)
> *Focus: How qubits interact to create non-local correlations.*

#### 1. The Tensor Product ($\otimes$)
To describe a system of multiple qubits, we use the Tensor Product. It combines individual state vectors into a larger system vector.
- **Rule:** $|a\rangle \otimes |b\rangle \rightarrow |ab\rangle$
- **Example:** Two qubits in state $|0\rangle$:
  $$|00\rangle = \begin{bmatrix} 1 \\ 0 \end{bmatrix} \otimes \begin{bmatrix} 1 \\ 0 \end{bmatrix} = \begin{bmatrix} 1 \\ 0 \\ 0 \\ 0 \end{bmatrix}$$
- **Binary Indexing:** The position of '1' in the vector corresponds to the binary value of the state (e.g., $|11\rangle \rightarrow 11_2 = 3 \rightarrow$ index 3).

#### 2. The CNOT Gate (Controlled-NOT)
The fundamental 2-qubit gate required for entanglement.
- **Matrix:**
  $$CNOT = \begin{bmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{bmatrix}$$
- **Logic:** If Control is $|1\rangle$, flip the Target. Note how the last two rows (representing $|10\rangle$ and $|11\rangle$) are swapped.

#### 3. Creating the Bell State (Proof)
The circuit `H(q0) -> CNOT(q0, q1)` creates entanglement:
1.  **Start:** $|00\rangle$
2.  **H on q0:** $\frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \otimes |0\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |10\rangle)$
3.  **CNOT (0 $\to$ 1):**
    - $|00\rangle \xrightarrow{C=0} |00\rangle$ (Unchanged)
    - $|10\rangle \xrightarrow{C=1} |11\rangle$ (Target flipped)
4.  **Result:**
    $$|\Phi^+\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}}$$
    *(Observation: Measuring one qubit instantly determines the state of the other).*

---

### Module 02: Single Qubit Gates (Day 2)
> *Focus: Manipulating individual quantum states.*

#### 1. The Pauli-X Gate (NOT Gate)
Rotates the state by $\pi$ around the X-axis (Bit Flip).
- **Matrix:**
  $$X = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}, \quad X|0\rangle = |1\rangle$$

#### 2. The Hadamard Gate (H)
Creates Superposition from basis states.
- **Matrix:**
  $$H = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}$$
- **Transformation:**
  $$H|0\rangle = |+\rangle = \frac{|0\rangle + |1\rangle}{\sqrt{2}}$$