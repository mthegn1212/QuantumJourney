# 🛸 Day 6: Deutsch's Algorithm

**Objective:** Determine if a function $f(x)$ is **Constant** or **Balanced** using only **1 query** (compared to 2 queries classically).

---

## 1. The Problem (Oracle)
We have a "Black Box" (Oracle) representing a function $f: \{0,1\} \to \{0,1\}$.
* **Constant:** $f(0) = f(1)$. (Outputs are identical).
* **Balanced:** $f(0) \neq f(1)$. (Outputs are opposite).

## 2. The Protocol
The algorithm uses 2 Qubits:
* $q_0$: Input qubit (Data).
* $q_1$: Helper qubit (Ancilla), initialized to $|-\rangle = \frac{|0\rangle - |1\rangle}{\sqrt{2}}$.

### Step-by-Step Flow
1.  **Initialization:** Start with $|0\rangle \otimes |1\rangle$.
2.  **Superposition:** Apply Hadamard (H) to both qubits.
    * $q_0 \to |+\rangle$ (Queries both 0 and 1 simultaneously).
    * $q_1 \to |-\rangle$ (Prepared for Phase Kickback).
3.  **Oracle Query ($U_f$):** Pass qubits through the Black Box.
    * Instead of flipping the *value* of $q_0$, the Oracle flips the *phase* of $q_0$ based on $f(x)$.
    * This is called **Phase Kickback**.
4.  **Interference (H on $q_0$):**
    * Apply H to $q_0$ to close the interference loop.
    * Constructive interference concentrates probability into one state.

### The Result
Measure Qubit $q_0$:
* **Result = 0:** Function is **Constant**.
* **Result = 1:** Function is **Balanced**.

---

## 3. Mathematical Proof (Simplified)
The final state of $q_0$ before measurement is:
$$|\psi_{final}\rangle = \pm |f(0) \oplus f(1)\rangle$$
* If Constant ($f(0) \oplus f(1) = 0$): We measure **|0>**.
* If Balanced ($f(0) \oplus f(1) = 1$): We measure **|1>**.