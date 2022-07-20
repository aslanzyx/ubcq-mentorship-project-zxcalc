# ubcq-mentorship-project-zxcalc

The mentorship project repo for UBC Quantum Club in 2022. The project is about simulating unitary circuit using ZX-calculus.

# Introduction to the project

The idea is to simulate quantum algorithms using a graph-based paradigm: ZX-calculus. We first map a unitary to an intermediate graph-based optimization lanugage: ZX-diagram. Each node on the ZX-diagram denotes a initial state, a unitary operator or a measurement. We use graph transformations to eliminate the nodes so that the computation is simulated.

## General procedure to (partially) simulate unitary circuits

1. Translate unitary circuit into **ZX-diagram**.
2. Perform **fusion** and **add/remove Hadamards** to reduce the ZX-diagram into a **graph state**.
3. Apply **local complementation** to remove **Clifford operations**
4. Apply **magic state decomposition** to map some non-Clifford operations to Clifford.
5. Execute the residual graph state:
  - The paper's approach: use magic state decomposition.
  - Another option: Map the ZX-diagram back to unitary circuit by finding **flow/gflow**.
  - Another option: use **measurement-based computation**(not covered in this project)

### Here's a quick intro: https://zxcalculus.com/intro.html

# Notes
We are refreshing the basic in the first 10 days. Many of the following algorithm might be familiar to you. You can find very detailed introduction with the qiskit textbook: https://qiskit.org/textbook/preface.html. specifically for the hidden shift circuit. I suggest you to check section 2 and 3 in the paper I listed there. I am pretty sure you can find lots of video lectures on youtube for most of algorithms listed. I will record some video over the weekend for hidden shift circuit.

For later content about stabilizer formalism, I suggest this class: Fault-tolerant quantum computation offered in 2021. The whole course content has been recorded with slides. Here's the course website: https://phas.ubc.ca/~raussen/Phys523/Phys523.html

# General schedule
## Reviews(optional):
- Searching algorithm:
  - Deutsch-Jozsa algorithm: https://qiskit.org/textbook/ch-algorithms/deutsch-jozsa.html
  - Grover's search: https://qiskit.org/textbook/ch-algorithms/grover.html
- QFT-based algorithms:
  - Quantum Fourier Transformation: https://qiskit.org/textbook/ch-algorithms/quantum-fourier-transform.html
  - Quantum Phase Estimation: https://qiskit.org/textbook/ch-algorithms/quantum-phase-estimation.html
  - Shor's algorithm: https://qiskit.org/textbook/ch-algorithms/shor.html
  - HHL algorithm: https://qiskit.org/textbook/ch-applications/hhl_tutorial.html
- Hidden shift problem:
  - Simon's algorithm: https://qiskit.org/textbook/ch-algorithms/simon.html
  - Hidden shift circuit: https://arxiv.org/abs/quant-ph/0211140

## Basics:
- Basics about qubits: https://youtu.be/H6xWOut0hek
- Stabilizer formalism: https://youtu.be/qrTrcfTewwo
- Some questions for you to think:
  1. Show `CNOT` and `CZ` are Clifford gates.
  2. What operator will you get when propagating a local(single-qubit) Clifford gate bypass a `CNOT` gate?
  3. What operator will you get when propagating a local non-Clifford gate bypass a `CNOT` gate?
  4. What happens if you measure the Bell state `(|00>+|11>)/sqrt(2)` with observable `X` or `Y`? Try to solve this using stabilizer formalism.
  5. Can you tell if a stabilizer state is entangled from its stabilizer generators?
  6. Upon local Pauli measurement on an entangled stabilizer state, are you able to obtain a deterministic outcome?(deterministic means you can sample a measurement outcome with 100% probability)
  7. Are the probabilities of local Pauli measurement fixed on an entangled stabilizer state?
  
## Graph State & MBQC
- Graph state & Local complementation: https://youtu.be/L2mnMjGaK2g
- Local complementation practices: https://youtu.be/64t8oHuGXxg
- Measurement-based quantum computation on graph state: https://youtu.be/zT2jw0D96Jw
- Flow condition: in the making
- Paper for flow conditions: https://arxiv.org/abs/quant-ph/0702212
- Some questions:
  1. Denote U as the local complementation operator. What is U^2? What is U^dagger? Why does U^dagger change the graph geometry the same way as U?
  2. How to reduce a projective measurement in X-base to Y-base? What graph trasformations need to be done to simulate an X-base measurement.
  3. Is U^2 actually a stabilizer operator? (Also this is a hint for Q1)
  4. What are the local complementation operations required to simulate 2 X-measurement on a pair of qubit sharing an edge. (It's the pivoting operation we introduced in lecture 4, but try to work that out yourself)
  5. Why can CZ and CNOT be mapped into each others by shifting wires? (hint: derive from a circuit implementation)
  6. Why can the control and target wire of CNOT be inverted by shifting wires? (hint: derive from a circuit implementation)
  7. Consider a half-way teleportation circuit, but the first qubit is measured on ZX-plane `cos(t)Z+sin(t)X`. What will happen? What if the first qubit is measured in YZ-plane `cos(t)Y+sin(t)Z`? What does the angle `t` correspond to?

## ZX-calculus & BSS decomposistion
