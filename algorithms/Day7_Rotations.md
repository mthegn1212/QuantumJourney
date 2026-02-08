# 🛸 Day 7: Parameterized Gates & Universal Rotations

**Objective:** Transition from fixed logic gates ($H, CX, X$) to Parameterized Quantum Circuits (PQC) using $R_x$ and $R_z$. This is the "bridge" to Quantum Machine Learning.

---

## 1. Beyond Fixed Gates
In classical-like algorithms (Deutsch, Grover), we use fixed oracles. In **QML**, we need to "tune" the circuit. This is done via **Rotation Gates**, where the angle $\theta$ acts as the model's weight.

### The $R_z(\theta)$ Gate (Phase Tuning)
The $R_z$ gate rotates the qubit state around the Z-axis of the Bloch Sphere. It modifies the **Phase** without changing the probability of measuring $|0\rangle$ or $|1\rangle$ directly—unless followed by an interference gate ($H$).
* **Matrix:** $$R_z(\theta) = \begin{bmatrix} e^{-i\theta/2} & 0 \\ 0 & e^{i\theta/2} \end{bmatrix}$$

### The $R_x(\theta)$ Gate (Amplitude Tuning)
The $R_x$ gate rotates the qubit around the X-axis. This gate **does** change the probability amplitudes.
* **Matrix:**
  $$R_x(\theta) = \begin{bmatrix} \cos(\theta/2) & -i\sin(\theta/2) \\ -i\sin(\theta/2) & \cos(\theta/2) \end{bmatrix}$$

---

## 2. Advanced Phase Kickback (Parameterized)
Using the logic from Day 6 (Deutsch), we can replace the fixed Oracle with a Parameterized $R_z$ gate to observe how phase shift affects the interference result.

### The Workflow:
1.  **State Prep:** $|0\rangle \to H \to |+\rangle$.
2.  **Rotation:** Apply $R_z(\theta)$ instead of a fixed $Z$ or Oracle.
3.  **Interference:** Apply $H$ again.
4.  **Observation:** The measurement outcome is no longer binary (0 or 1) by nature, but a function of $\theta$.

---

## 3. Implementation Example (PennyLane)
This script demonstrates how $R_z$ and $R_x$ influence the final state, which is the foundation for building a **Quantum Neural Network**.

```python
import pennylane as qml
from pennylane import numpy as np

# Define a 1-qubit device
dev = qml.device("default.qubit", wires=1)

@qml.qnode(dev)
def parameterized_circuit(theta_1, theta_2):
    # Apply a rotation around X (Amplitude tuning)
    qml.RX(theta_1, wires=0)
    
    # Apply a rotation around Z (Phase tuning)
    qml.RZ(theta_2, wires=0)
    
    # Return the expectation value (The "Output" of our mini-model)
    return qml.expval(qml.PauliZ(0))

# Example Execution
t1, t2 = np.pi/4, np.pi/2
output = parameterized_circuit(t1, t2)

print(f"--- Day 7: Parameterized Output ---")
print(f"Theta_1 (RX): {t1:.4f} | Theta_2 (RZ): {t2:.4f}")
print(f"Model Output: {output:.4f}")