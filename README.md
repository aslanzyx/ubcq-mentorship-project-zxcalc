# ubcq-mentorship-project-zxcalc
The mentorship project repo for UBC Quantum Club in 2022. The project is about simulating unitary circuit using ZX-calculus.

# Introduction to the project

The idea is to simulate quantum algorithms using a graph-based paradigm: ZX-calculus. We first map a unitary to an intermediate graph-based optimization lanugage: ZX-diagram. Each node on the ZX-diagram denotes a initial state, a unitary operator or a measurement. We use graph transformations to eliminate the nodes so that the computation is simulated.

## General procedure to (partially) simulate unitary circuits

1. Translate unitary circuit into **ZX-diagram**.
2. Perform **fusion** and **add/remove Hadamards** to reduce the ZX-diagram into a **graph state**.
3. Apply **local complementation** to remove **Clifford operations**
4. Apply **magic state decomposition** to map some non-Clifford operations to Clifford.
5. Map the ZX-diagram back to unitary circuit by finding **flow/gflow**.
6. Another option: use **measurement-based computation**(not covered in this project)

### Here's a quick intro: https://zxcalculus.com/intro.html

# Notes
We are refreshing the basic in the first 10 days. Many of the following algorithm might be familiar to you. You can find very detailed introduction with the qiskit textbook: https://qiskit.org/textbook/preface.html. specifically for the hidden shift circuit. I suggest you to check section 2 and 3 in the paper I listed there. I am pretty sure you can find lots of video lectures on youtube for most of algorithms listed. I will record some video over the weekend for hidden shift circuit.

For later content about stabilizer formalism, I suggest this class: Fault-tolerant quantum computation offered in 2021. The whole course content has been recorded with slides. Here's the course website: https://phas.ubc.ca/~raussen/Phys523/Phys523.html

# General schedule
- Until June 20:
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
- Until June 27:
  - Basics about qubits: https://youtu.be/H6xWOut0hek
  - Stabilizer formalism: 
  - Some practices:
    - Show `CNOT` and `CZ` are Clifford operations.
    - What happens if you measure the Bell state `(|00>+|11>)/sqrt(2)` with observable `X` or `Y`? Try to solve this using stabilizer formalism.
    - Can you tell if a stabilizer state is entangled from its stabilizer generators?
    - Upon local(single-qubit) Pauli measurement on an entangled stabilizer state, are you able to obtain a deterministic outcome?(deterministic means you obtained a measurement outcome with 100% probability)
- Until July 4:
  - Graph state
  - Local complementation
- Until July 11:
  - Measurement-based quantum computation on graph state
  - Simulating Pauli measurements on graph state
- Until July 18:
  - ZX-calculus
  - Graph state in ZX-diagram
- Until July 25:
  - Circuit extraction from ZX-diagram
- Until August 1:
  - learn PyZX API
- TBD later
