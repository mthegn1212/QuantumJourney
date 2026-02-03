# Quantum Algorithms & Protocols 🚀

This directory focuses on the implementation of standard quantum protocols and algorithms, bridging the gap between theory and application.

## 📂 Module Index

| Sequence | Notebook File | Key Concepts |
| :--- | :--- | :--- |
| **01** | `01_Quantum_Teleportation.ipynb` | **Teleportation Protocol**, No-Cloning Theorem, Bell Measurement, Classical Communication. |

---

## 📚 Protocol Deep Dive: Quantum Teleportation

### Objective
Transmit an unknown quantum state $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ from Alice to Bob using **Entanglement** and **Classical Communication**.

> **Note:** This protocol does *not* transport matter or energy. The original state at Alice's side is destroyed during the process, adhering to the **No-Cloning Theorem**.

### The 4-Step Process

#### 1. Initialization (The Channel)
Alice and Bob share an entangled pair (Bell Pair):
$$|\text{Bell}\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}}$$

#### 2. Encoding (Alice's Side)
Alice interacts her payload qubit ($|\psi\rangle$) with her half of the entangled pair using:
- **CNOT Gate**
- **Hadamard Gate**

#### 3. Measurement & Transmission
Alice measures her two qubits and obtains two classical bits ($00, 01, 10, 11$). She sends these bits to Bob via a classical channel (e.g., internet).

#### 4. Decoding (Bob's Correction)
Bob applies a specific gate to his qubit based on Alice's message to recover $|\psi\rangle$:

| Alice's Bits | Bob's Action | Logic Gate |
| :---: | :--- | :---: |
| **00** | Do nothing | $I$ |
| **01** | Bit Flip | $X$ |
| **10** | Phase Flip | $Z$ |
| **11** | Bit & Phase Flip | $ZX$ |