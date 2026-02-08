# 🌌 Phase 1: Quantum Foundations & Parameterized Logic

## 🎯 Objective
This phase transitions from fixed logic gates to **Parameterized Quantum Circuits (PQC)**. By completing this project, the goal is to validate the understanding of entanglement and phase manipulation before moving to Phase 2 (QML).

---

## 🏗️ Final Project Requirements

### Part 1: Architecture
Implement a 3-qubit circuit with the following structural layers:

1. **Entanglement Layer:** Construct a **GHZ State** ($|GHZ\rangle = \frac{|000\rangle + |111\rangle}{\sqrt{2}}$) as the quantum backbone.
2. **Encoding Layer (The "Warmth" Factor):** - Apply $R_z(\theta)$ on Qubit 0 (Targeting Phase).
    - Apply $R_x(\phi)$ on Qubit 1 (Targeting Amplitude).
3. **Interference Layer:** Apply Hadamard gates to all qubits to prepare for final measurement and induce interference.

### Part 2: Research & Analysis
*To be documented in your Final Report:*
- **The Bloch Shift:** Contrast the resulting state of $|+\rangle$ after an $X$ gate versus an $R_z(\pi)$ gate. Explain the physical difference on the Bloch Sphere.
- **Circuit Depth:** Calculate the minimum depth required to prepare a 3-qubit GHZ state.
- **QML Mapping:** Propose a method to map real-world data (e.g., Temperature from *PlantDoctor*) into the angles $\theta$ and $\phi$.