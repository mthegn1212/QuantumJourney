# 🛸 Day 4: Quantum Teleportation (Theory)

**Objective:** Transfer a quantum state $|\psi\rangle$ from Alice to Bob using only 2 classical bits and an entangled Bell Pair.

---

## 1. The Math Behind It
The teleportation protocol relies on manipulating a 3-Qubit system:
* $q_0$: The Message (Alice)
* $q_1$: Alice's entangled qubit
* $q_2$: Bob's entangled qubit

### General Equation (Before Measurement)
After Alice performs the CNOT and Hadamard operations, the system is in a superposition of 4 possible scenarios:

$$
|\Psi_2\rangle = \frac{1}{2} [
    \underbrace{|00\rangle}_{Alice} (\alpha|0\rangle + \beta|1\rangle)_{Bob} +
    \underbrace{|01\rangle}_{Alice} (\alpha|1\rangle + \beta|0\rangle)_{Bob} +
    \underbrace{|10\rangle}_{Alice} (\alpha|0\rangle - \beta|1\rangle)_{Bob} +
    \underbrace{|11\rangle}_{Alice} (\alpha|1\rangle - \beta|0\rangle)_{Bob}
]
$$

> **Note:** The factor $\frac{1}{2}$ represents probability amplitudes. When Alice measures her qubits, the system **collapses** into one of the 4 branches above with a 25% probability each.

---

## 2. Correction Table (The "Cheat Sheet")
Which quantum gate must Bob apply to recover the original message? It depends entirely on Alice's measurement result:

| Alice Sends (Bits) | State Bob Receives | The Error | Correction Gate |
| :---: | :---: | :---: | :---: |
| **00** | $\alpha|0\rangle + \beta|1\rangle$ | None | **I** (Do nothing) |
| **01** | $\alpha|1\rangle + \beta|0\rangle$ | Bit Flip | **X Gate** |
| **10** | $\alpha|0\rangle - \beta|1\rangle$ | Phase Flip | **Z Gate** |
| **11** | $\alpha|1\rangle - \beta|0\rangle$ | Both | **Z *then* X** |

---

## 3. Why 2 Classical Bits?
The **No-Cloning Theorem** forbids copying an unknown quantum state. To "teleport," we must destroy the original state at the source (Alice's measurement collapses the state) and reconstruct it at the destination (Bob's correction). The 2 classical bits are the key that tells Bob *how* to reconstruct it.