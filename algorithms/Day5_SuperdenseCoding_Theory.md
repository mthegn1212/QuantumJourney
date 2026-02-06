# 🛸 Day 5: Superdense Coding

**Objective:** Transmit **2 classical bits** of information from Alice to Bob by sending only **1 physical Qubit**.

---

## 1. Mechanism
This is the inverse protocol of Quantum Teleportation.
* **Teleportation:** 1 Qubit $\to$ 2 Classical Bits.
* **Superdense Coding:** 2 Classical Bits $\to$ 1 Qubit.

### System Setup
* **Alice:** Holds Qubit $q_0$.
* **Bob:** Holds Qubit $q_1$.
* **Initial Shared State:** Bell State $|\Phi^+\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}}$.

---

## 2. Step-by-Step Protocol

### Step 1: Alice's Encoding
Depending on the 2-bit message Alice wants to send, she applies a specific quantum gate to **her qubit ($q_0$)**. This transforms the shared Bell state into one of the 4 orthogonal Bell states.

| Message to Send | Gate on $q_0$ | Resulting State | Math Formula |
| :---: | :---: | :---: | :--- |
| **00** | **I** (Identity) | $|\Phi^+\rangle$ | $\frac{|00\rangle + |11\rangle}{\sqrt{2}}$ |
| **01** | **Z** (Phase Flip) | $|\Phi^-\rangle$ | $\frac{|00\rangle - |11\rangle}{\sqrt{2}}$ |
| **10** | **X** (Bit Flip) | $|\Psi^+\rangle$ | $\frac{|01\rangle + |10\rangle}{\sqrt{2}}$ |
| **11** | **Z *then* X** | $|\Psi^-\rangle$ | $\frac{|01\rangle - |10\rangle}{\sqrt{2}}$ |

*(Note: Qiskit uses little-endian ordering. The rightmost bit is qubit 0).*

### Step 2: Transmission
Alice sends her qubit ($q_0$) physically to Bob.
$\rightarrow$ Bob now possesses both $q_0$ and $q_1$.

### Step 3: Bob's Decoding
To read the information, Bob must "disentangle" the system. He performs the reverse of the Bell preparation circuit:

1.  **CNOT ($q_0 \to q_1$):** Unravels the bit flip correlation.
2.  **Hadamard ($q_0$):** Unravels the superposition (converts X-basis back to Z-basis).

### Step 4: Measurement
After decoding, the system collapses into a simple product state $|ab\rangle$.
* If state was $|\Phi^+\rangle$ $\xrightarrow{\text{Decode}}$ $|00\rangle$.
* If state was $|\Psi^-\rangle$ $\xrightarrow{\text{Decode}}$ $|11\rangle$.

$\rightarrow$ Bob measures the qubits and retrieves the exact 2 bits Alice intended to send.