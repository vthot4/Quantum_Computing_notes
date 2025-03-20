# Linear Algebra for Quantum Computing

This document provides a comprehensive overview of the linear algebra concepts necessary for understanding quantum computing. We'll explore these concepts with clear explanations and examples to build a solid foundation for quantum computing studies.

## Table of Contents
1. [Complex Numbers](#complex-numbers)
2. [Vectors and Vector Spaces](#vectors-and-vector-spaces)
3. [Dirac Notation (Bra-Ket)](#dirac-notation-bra-ket)
4. [Matrices and Linear Transformations](#matrices-and-linear-transformations)
5. [Inner Products and Norms](#inner-products-and-norms)
6. [Eigenvalues and Eigenvectors](#eigenvalues-and-eigenvectors)
7. [Pauli Matrices](#pauli-matrices)
8. [Abelian Sets](#abelian-sets)
9. [Tensor Products](#tensor-products)
10. [Quantum Circuits and Linear Algebra](#quantum-circuits-and-linear-algebra)

## Complex Numbers

Complex numbers are fundamental to quantum computing. A complex number has the form $a + bi$ where $a$ and $b$ are real numbers, and $i$ is the imaginary unit with the property $i^2 = -1$.

### Properties of Complex Numbers

- **Addition**: $(a + bi) + (c + di) = (a + c) + (b + d)i$
- **Multiplication**: $(a + bi)(c + di) = (ac - bd) + (ad + bc)i$
- **Complex Conjugate**: The complex conjugate of $z = a + bi$ is $z^* = a - bi$
- **Absolute Value (Modulus)**: $|z| = |a + bi| = \sqrt{a^2 + b^2}$
- **Polar Form**: $z = a + bi = |z|e^{i\theta}$ where $\theta = \arctan(b/a)$ is the phase

### Examples!! 

Consider the complex number $z = 3 + 4i$:
- Its complex conjugate is $z^* = 3 - 4i$
- Its absolute value is $|z| = \sqrt{3^2 + 4^2} = \sqrt{25} = 5$
- Its phase is $\theta = \arctan(4/3) \approx 0.927$ radians or about $53.1$ degrees
- In polar form: $z = 5e^{i \cdot 0.927}$

### Complex Numbers in Quantum Computing

In quantum computing, complex numbers are essential because:

1. **Quantum Amplitudes**: The coefficients in quantum state vectors are complex numbers called amplitudes.
2. **Interference**: Complex amplitudes allow for quantum interference effects, where probability amplitudes can add constructively or destructively.
3. **Phase Information**: The phase of complex numbers encodes important information in quantum states that affects interference patterns.
4. **Unitary Transformations**: Quantum gates are represented by unitary matrices with complex entries.

### Euler's Formula and Quantum Phases

Euler's formula provides a fundamental connection between complex exponentials and trigonometric functions:

$$e^{i\theta} = \cos\theta + i\sin\theta$$

This is particularly important in quantum computing for representing phases:

- A global phase $e^{i\phi}|\psi\rangle$ doesn't affect measurement probabilities
- Relative phases between components of a quantum state do affect measurement outcomes

## Vectors and Vector Spaces

In quantum computing, quantum states are represented as vectors in a complex vector space. A vector space is a set of vectors that can be added together and multiplied by scalars (numbers).

### Key Concepts

- **Vector**: An ordered list of numbers (components). In quantum computing, these components are typically complex numbers.
- **Vector Space**: A set of vectors that is closed under vector addition and scalar multiplication.
- **Basis**: A set of linearly independent vectors that can represent any vector in the space through linear combinations.
- **Dimension**: The number of vectors in a basis for the vector space.
- **Linear Independence**: A set of vectors is linearly independent if none of them can be expressed as a linear combination of the others.
- **Span**: The set of all possible linear combinations of a set of vectors.

### Formal Definition of a Vector Space

A vector space $V$ over a field $F$ (usually $\mathbb{R}$ or $\mathbb{C}$) is a set with two operations:
1. Vector addition: $+: V \times V \rightarrow V$
2. Scalar multiplication: $\cdot: F \times V \rightarrow V$

These operations must satisfy eight axioms:
1. Commutativity: $\vec{u} + \vec{v} = \vec{v} + \vec{u}$
2. Associativity (addition): $(\vec{u} + \vec{v}) + \vec{w} = \vec{u} + (\vec{v} + \vec{w})$
3. Additive identity: There exists $\vec{0} \in V$ such that $\vec{v} + \vec{0} = \vec{v}$ for all $\vec{v} \in V$
4. Additive inverse: For each $\vec{v} \in V$, there exists $-\vec{v} \in V$ such that $\vec{v} + (-\vec{v}) = \vec{0}$
5. Associativity (scalar multiplication): $a(b\vec{v}) = (ab)\vec{v}$
6. Distributivity (scalar): $(a + b)\vec{v} = a\vec{v} + b\vec{v}$
7. Distributivity (vector): $a(\vec{u} + \vec{v}) = a\vec{u} + a\vec{v}$
8. Scalar identity: $1\vec{v} = \vec{v}$

### Hilbert Space

In quantum mechanics, quantum states live in a special type of vector space called a Hilbert space, which is a complete inner product space. The key features of a Hilbert space are:

1. It's a vector space over complex numbers
2. It has an inner product operation
3. It's complete (all Cauchy sequences converge)

For finite-dimensional quantum systems (like qubits), we work with finite-dimensional Hilbert spaces, which are essentially $\mathbb{C}^n$ with the standard inner product.

### Quantum State Vectors

In quantum computing, an n-qubit system is represented by a vector in a $2^n$-dimensional complex vector space. The standard basis for a single qubit consists of:

- $|0\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$ (representing the "0" state)
- $|1\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$ (representing the "1" state)

A general single-qubit state can be written as:

$$|\psi\rangle = \alpha|0\rangle + \beta|1\rangle = \begin{pmatrix} \alpha \\ \beta \end{pmatrix}$$

where $\alpha$ and $\beta$ are complex numbers satisfying $|\alpha|^2 + |\beta|^2 = 1$ (normalization condition).

### The Bloch Sphere Representation

Any single-qubit pure state can be represented as a point on the Bloch sphere:

$$|\psi\rangle = \cos\frac{\theta}{2}|0\rangle + e^{i\phi}\sin\frac{\theta}{2}|1\rangle$$

where:
- $\theta \in [0, \pi]$ is the polar angle from the z-axis
- $\phi \in [0, 2\pi)$ is the azimuthal angle in the xy-plane

This provides a geometric visualization of single-qubit states:
- $|0\rangle$ is at the north pole
- $|1\rangle$ is at the south pole
- States on the equator, like $|+\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)$, have equal probabilities of measuring 0 or 1

### Examples of Quantum States

1. **Equal Superposition**:
   $|+\rangle = \frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix}$
   
   This state has a 50% probability of measuring either 0 or 1.

2. **Phase Superposition**:
   $|-\rangle = \frac{1}{\sqrt{2}}|0\rangle - \frac{1}{\sqrt{2}}|1\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ -1 \end{pmatrix}$
   
   This state also has a 50% probability of measuring either 0 or 1, but differs from $|+\rangle$ by a relative phase.

3. **Two-Qubit Bell State**:
   $|\Phi^+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle) = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 0 \\ 0 \\ 1 \end{pmatrix}$
   
   This is a maximally entangled state where measuring one qubit instantly determines the state of the other.

## Dirac Notation (Bra-Ket)

Dirac notation, also known as bra-ket notation, is a standard notation used in quantum mechanics and quantum computing to represent quantum states and operations.

### Key Elements

- **Ket**: A column vector denoted by $|\psi\rangle$, representing a quantum state.
- **Bra**: A row vector denoted by $\langle\psi|$, representing the conjugate transpose (Hermitian conjugate) of the corresponding ket.
- **Bra-Ket**: The inner product of two vectors, denoted by $\langle\phi|\psi\rangle$.
- **Ket-Bra**: The outer product of two vectors, denoted by $|\psi\rangle\langle\phi|$, resulting in a matrix.

### Mathematical Representation

If $|\psi\rangle = \begin{pmatrix} \alpha \\ \beta \end{pmatrix}$, then $\langle\psi| = \begin{pmatrix} \alpha^* & \beta^* \end{pmatrix}$ (where $*$ denotes complex conjugation).

The inner product $\langle\phi|\psi\rangle$ is calculated as:

$$\langle\phi|\psi\rangle = \begin{pmatrix} \gamma^* & \delta^* \end{pmatrix} \begin{pmatrix} \alpha \\ \beta \end{pmatrix} = \gamma^*\alpha + \delta^*\beta$$

where $|\phi\rangle = \begin{pmatrix} \gamma \\ \delta \end{pmatrix}$.

The outer product $|\psi\rangle\langle\phi|$ is calculated as:

$$|\psi\rangle\langle\phi| = \begin{pmatrix} \alpha \\ \beta \end{pmatrix} \begin{pmatrix} \gamma^* & \delta^* \end{pmatrix} = \begin{pmatrix} \alpha\gamma^* & \alpha\delta^* \\ \beta\gamma^* & \beta\delta^* \end{pmatrix}$$

### Dirac Notation for Multi-Qubit Systems

For multi-qubit systems, we use tensor products of single-qubit states:

- $|0\rangle \otimes |0\rangle = |00\rangle$
- $|0\rangle \otimes |1\rangle = |01\rangle$
- $|1\rangle \otimes |0\rangle = |10\rangle$
- $|1\rangle \otimes |1\rangle = |11\rangle$

### Operators in Dirac Notation

Quantum operators (gates) can be expressed in Dirac notation:

- Identity operator: $I = |0\rangle\langle 0| + |1\rangle\langle 1|$
- Pauli-X: $X = |0\rangle\langle 1| + |1\rangle\langle 0|$
- Pauli-Z: $Z = |0\rangle\langle 0| - |1\rangle\langle 1|$
- Hadamard: $H = \frac{1}{\sqrt{2}}(|0\rangle\langle 0| + |0\rangle\langle 1| + |1\rangle\langle 0| - |1\rangle\langle 1|)$

### Projection Operators

Projection operators project a state onto a subspace. For a state $|\psi\rangle$, the projection operator is:

$$P_\psi = |\psi\rangle\langle\psi|$$

For example, the projector onto the $|0\rangle$ state is:

$$P_0 = |0\rangle\langle 0| = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}$$

Applying this to a state $|\phi\rangle = \alpha|0\rangle + \beta|1\rangle$:

$$P_0|\phi\rangle = |0\rangle\langle 0|\phi\rangle = |0\rangle\langle 0|(\alpha|0\rangle + \beta|1\rangle) = \alpha|0\rangle$$

This projects the state onto the $|0\rangle$ component.

## Matrices and Linear Transformations

In quantum computing, operations on quantum states are represented by matrices. These matrices represent linear transformations of the vector space.

### Key Concepts

- **Linear Transformation**: A function that preserves vector addition and scalar multiplication.
- **Matrix Representation**: A linear transformation can be represented by a matrix.
- **Unitary Matrix**: A matrix $U$ such that $U^\dagger U = UU^\dagger = I$, where $U^\dagger$ is the conjugate transpose of $U$ and $I$ is the identity matrix. Quantum operations must be unitary to preserve the normalization of quantum states.
- **Hermitian Matrix**: A matrix $H$ such that $H = H^\dagger$. Hermitian matrices represent observable quantities in quantum mechanics.
- **Positive Semidefinite Matrix**: A Hermitian matrix whose eigenvalues are all non-negative.

### Matrix Properties Important for Quantum Computing

1. **Unitarity**: Ensures probability conservation in quantum evolution
2. **Hermiticity**: Ensures real eigenvalues for physical observables
3. **Tensor Product Structure**: Allows representation of composite quantum systems
4. **Trace Properties**: Important for calculating expectation values and partial measurements

### Common Quantum Gates as Matrices

1. **Pauli-X Gate (NOT Gate)**:
   $$X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$$

2. **Pauli-Y Gate**:
   $$Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}$$

3. **Pauli-Z Gate**:
   $$Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$$

4. **Hadamard Gate**:
   $$H = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$$

5. **Phase Gate (S Gate)**:
   $$S = \begin{pmatrix} 1 & 0 \\ 0 & i \end{pmatrix}$$

6. **π/8 Gate (T Gate)**:
   $$T = \begin{pmatrix} 1 & 0 \\ 0 & e^{i\pi/4} \end{pmatrix}$$

7. **Controlled-NOT (CNOT) Gate**:
   $$\text{CNOT} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}$$

### Matrix Decompositions in Quantum Computing

1. **Spectral Decomposition**:
   Any Hermitian matrix $H$ can be decomposed as:
   $$H = \sum_i \lambda_i |v_i\rangle\langle v_i|$$
   where $\lambda_i$ are the eigenvalues and $|v_i\rangle$ are the corresponding eigenvectors.

2. **Singular Value Decomposition (SVD)**:
   Any matrix $M$ can be decomposed as:
   $$M = U\Sigma V^\dagger$$
   where $U$ and $V$ are unitary matrices and $\Sigma$ is a diagonal matrix of singular values.

### Example: Applying the Hadamard Gate

Applying the Hadamard gate to the $|0\rangle$ state:

$$H|0\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}\begin{pmatrix} 1 \\ 0 \end{pmatrix} = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix} = |+\rangle$$

This creates an equal superposition of $|0\rangle$ and $|1\rangle$.

Applying the Hadamard gate again returns to the original state:

$$H|+\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix} = \begin{pmatrix} 1 \\ 0 \end{pmatrix} = |0\rangle$$

## Inner Products and Norms

The inner product of two vectors gives a measure of their similarity. In quantum computing, the inner product is used to calculate the probability of measuring a particular state.

### Key Concepts

- **Inner Product**: For complex vectors, the inner product $\langle\phi|\psi\rangle$ is the sum of the products of corresponding components, with the first vector's components conjugated.
- **Norm**: The norm of a vector $|\psi\rangle$ is $\sqrt{\langle\psi|\psi\rangle}$, which gives a measure of its "length."
- **Normalization**: A vector is normalized if its norm equals 1. Quantum state vectors must be normalized.
- **Orthogonality**: Two vectors are orthogonal if their inner product is zero.
- **Orthonormal Basis**: A basis where all vectors are normalized and mutually orthogonal.

### Properties of Inner Products

For vectors $|\psi\rangle$, $|\phi\rangle$, and $|\chi\rangle$, and scalars $\alpha$ and $\beta$:

1. **Conjugate Symmetry**: $\langle\phi|\psi\rangle = \langle\psi|\phi\rangle^*$
2. **Linearity in Second Argument**: $\langle\phi|(\alpha|\psi\rangle + \beta|\chi\rangle) = \alpha\langle\phi|\psi\rangle + \beta\langle\phi|\chi\rangle$
3. **Anti-linearity in First Argument**: $(\alpha\langle\phi| + \beta\langle\chi|)|\psi\rangle = \alpha^*\langle\phi|\psi\rangle + \beta^*\langle\chi|\psi\rangle$
4. **Positive Definiteness**: $\langle\psi|\psi\rangle \geq 0$, with equality if and only if $|\psi\rangle = 0$

### Probability Interpretation

In quantum mechanics, if $|\psi\rangle$ is a normalized state vector and $\{|i\rangle\}$ is an orthonormal basis, then:

- $|\langle i|\psi\rangle|^2$ is the probability of measuring the state $|i\rangle$ when the system is in state $|\psi\rangle$
- $\sum_i |\langle i|\psi\rangle|^2 = 1$ (total probability is 1)

### Example: Measuring a Superposition State

Consider the state $|\psi\rangle = \frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle$:

- Probability of measuring $|0\rangle$: $|\langle 0|\psi\rangle|^2 = \left|\frac{1}{\sqrt{2}}\right|^2 = \frac{1}{2}$
- Probability of measuring $|1\rangle$: $|\langle 1|\psi\rangle|^2 = \left|\frac{1}{\sqrt{2}}\right|^2 = \frac{1}{2}$

### Example: Orthogonal States

Consider the vectors $|\psi\rangle = \frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle$ and $|\phi\rangle = \frac{1}{\sqrt{2}}|0\rangle - \frac{1}{\sqrt{2}}|1\rangle$.

The inner product $\langle\phi|\psi\rangle$ is:

$$\langle\phi|\psi\rangle = \left(\frac{1}{\sqrt{2}}\right)^* \left(\frac{1}{\sqrt{2}}\right) + \left(-\frac{1}{\sqrt{2}}\right)^* \left(\frac{1}{\sqrt{2}}\right) = \frac{1}{2} - \frac{1}{2} = 0$$

This means $|\psi\rangle$ and $|\phi\rangle$ are orthogonal. In quantum computing, orthogonal states are perfectly distinguishable by measurement.

## Eigenvalues and Eigenvectors

Eigenvalues and eigenvectors are crucial concepts in quantum computing, particularly for understanding quantum measurements and the time evolution of quantum systems.

### Key Concepts

- **Eigenvector**: A non-zero vector $|v\rangle$ such that when a linear transformation (matrix) $A$ is applied to it, the result is a scalar multiple of the vector: $A|v\rangle = \lambda|v\rangle$.
- **Eigenvalue**: The scalar $\lambda$ in the equation $A|v\rangle = \lambda|v\rangle$.
- **Characteristic Equation**: The equation $\det(A - \lambda I) = 0$ whose solutions are the eigenvalues of $A$.
- **Eigenspace**: The set of all eigenvectors corresponding to a particular eigenvalue, plus the zero vector.
- **Spectral Decomposition**: A Hermitian matrix can be decomposed as $A = \sum_i \lambda_i |v_i\rangle\langle v_i|$, where $\lambda_i$ are the eigenvalues and $|v_i\rangle$ are the corresponding eigenvectors.

### Properties of Eigenvalues and Eigenvectors

1. **For Hermitian Matrices**:
   - All eigenvalues are real
   - Eigenvectors corresponding to different eigenvalues are orthogonal
   - The matrix can be diagonalized by a unitary transformation

2. **For Unitary Matrices**:
   - All eigenvalues have magnitude 1 (they are of the form $e^{i\theta}$)
   - Eigenvectors corresponding to different eigenvalues are orthogonal
   - The matrix can be diagonalized by a unitary transformation

### Significance in Quantum Computing

- **Measurements**: When a quantum observable (represented by a Hermitian matrix) is measured, the possible outcomes are the eigenvalues of the matrix.
- **Quantum States After Measurement**: After measuring an observable and obtaining an eigenvalue $\lambda_i$, the quantum state collapses to the corresponding eigenvector $|v_i\rangle$.
- **Time Evolution**: The time evolution of a quantum system is determined by the eigenvalues and eigenvectors of its Hamiltonian.
- **Quantum Algorithms**: Many quantum algorithms, such as quantum phase estimation, rely on finding eigenvalues of unitary operators.

### Example: Eigendecomposition of the Hadamard Gate

The Hadamard gate $H = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$ has:

- Eigenvalues: $\lambda_1 = 1$ and $\lambda_2 = -1$
- Corresponding eigenvectors: $|v_1\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix}$ and $|v_2\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ -1 \end{pmatrix}$

The spectral decomposition of $H$ is:

$$H = 1 \cdot |v_1\rangle\langle v_1| + (-1) \cdot |v_2\rangle\langle v_2|$$

### Example: Pauli-Z Measurement

The Pauli-Z matrix $Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$ has:
- Eigenvalues: $\lambda_1 = 1$ and $\lambda_2 = -1$
- Corresponding eigenvectors: $|v_1\rangle = |0\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$ and $|v_2\rangle = |1\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$

When the Z-measurement is performed on a qubit in state $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$:
- The outcome will be either +1 or -1
- The probability of getting +1 is $|\alpha|^2$, and the state collapses to $|0\rangle$
- The probability of getting -1 is $|\beta|^2$, and the state collapses to $|1\rangle$

## Pauli Matrices

Pauli matrices are a set of three 2×2 complex matrices that are Hermitian and unitary. They are fundamental in quantum computing as they form a basis for the space of 2×2 Hermitian matrices and represent single-qubit quantum gates.

### The Three Pauli Matrices

1. **Pauli-X (σₓ)**:
   $$\sigma_x = X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$$
   - Acts as a bit-flip (NOT gate)
   - Rotates the qubit state around the x-axis of the Bloch sphere by π radians

2. **Pauli-Y (σᵧ)**:
   $$\sigma_y = Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}$$
   - Rotates the qubit state around the y-axis of the Bloch sphere by π radians

3. **Pauli-Z (σᵤ)**:
   $$\sigma_z = Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$$
   - Acts as a phase-flip
   - Rotates the qubit state around the z-axis of the Bloch sphere by π radians

### The Identity Matrix

Often included with the Pauli matrices is the 2×2 identity matrix:

$$I = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$$

Together, $\{I, X, Y, Z\}$ form a basis for the space of 2×2 Hermitian matrices.

### Properties of Pauli Matrices

1. **Hermitian**: Each Pauli matrix is equal to its conjugate transpose: $\sigma_i = \sigma_i^\dagger$
2. **Unitary**: Each Pauli matrix is unitary: $\sigma_i\sigma_i^\dagger = \sigma_i^\dagger\sigma_i = I$
3. **Determinant**: Each Pauli matrix has determinant -1
4. **Trace**: Each Pauli matrix has trace 0
5. **Square**: The square of each Pauli matrix is the identity matrix: $\sigma_i^2 = I$
6. **Anticommutation**: Pauli matrices anticommute with each other: $\sigma_i\sigma_j = -\sigma_j\sigma_i$ for $i \neq j$
7. **Multiplication**: The product of any two different Pauli matrices gives the third, multiplied by $i$ or $-i$:
   - $\sigma_x\sigma_y = i\sigma_z$
   - $\sigma_y\sigma_z = i\sigma_x$
   - $\sigma_z\sigma_x = i\sigma_y$
8. **Commutation Relations**: The Pauli matrices satisfy the commutation relations:
   $$[\sigma_i, \sigma_j] = 2i\epsilon_{ijk}\sigma_k$$
   where $\epsilon_{ijk}$ is the Levi-Civita symbol.

### Pauli Group

The Pauli group $\mathcal{P}_1$ for a single qubit consists of the Pauli matrices and the identity, with possible phases $\{\pm 1, \pm i\}$:

$$\mathcal{P}_1 = \{\pm I, \pm iI, \pm X, \pm iX, \pm Y, \pm iY, \pm Z, \pm iZ\}$$

For $n$ qubits, the Pauli group $\mathcal{P}_n$ consists of tensor products of elements from $\mathcal{P}_1$:

$$\mathcal{P}_n = \{P_1 \otimes P_2 \otimes \cdots \otimes P_n : P_j \in \mathcal{P}_1\}$$

The Pauli group is fundamental in quantum error correction, particularly in the stabilizer formalism.

### Example: Pauli Matrices in Action

Consider a qubit in the state $|0\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$:

1. Applying Pauli-X:
   $$X|0\rangle = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}\begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 0 \\ 1 \end{pmatrix} = |1\rangle$$
   This flips the state from $|0\rangle$ to $|1\rangle$.

2. Applying Pauli-Z:
   $$Z|0\rangle = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}\begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 1 \\ 0 \end{pmatrix} = |0\rangle$$
   This leaves $|0\rangle$ unchanged.

3. Applying Pauli-Z to $|1\rangle$:
   $$Z|1\rangle = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}\begin{pmatrix} 0 \\ 1 \end{pmatrix} = \begin{pmatrix} 0 \\ -1 \end{pmatrix} = -|1\rangle$$
   This adds a phase of -1 to $|1\rangle$.

4. Applying Pauli-Y to $|0\rangle$:
   $$Y|0\rangle = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}\begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 0 \\ i \end{pmatrix} = i|1\rangle$$
   This flips the state from $|0\rangle$ to $|1\rangle$ and adds a phase of $i$.

### Pauli Matrices and Rotations

The Pauli matrices generate rotations around the x, y, and z axes of the Bloch sphere:

1. **Rotation around x-axis**:
   $$R_x(\theta) = e^{-i\theta X/2} = \cos(\theta/2)I - i\sin(\theta/2)X = \begin{pmatrix} \cos(\theta/2) & -i\sin(\theta/2) \\ -i\sin(\theta/2) & \cos(\theta/2) \end{pmatrix}$$

2. **Rotation around y-axis**:
   $$R_y(\theta) = e^{-i\theta Y/2} = \cos(\theta/2)I - i\sin(\theta/2)Y = \begin{pmatrix} \cos(\theta/2) & -\sin(\theta/2) \\ \sin(\theta/2) & \cos(\theta/2) \end{pmatrix}$$

3. **Rotation around z-axis**:
   $$R_z(\theta) = e^{-i\theta Z/2} = \cos(\theta/2)I - i\sin(\theta/2)Z = \begin{pmatrix} e^{-i\theta/2} & 0 \\ 0 & e^{i\theta/2} \end{pmatrix}$$

These rotation operators are fundamental in quantum computing for implementing arbitrary single-qubit gates.

## Abelian Sets

An Abelian set in quantum computing refers to a set of operators (matrices) that all commute with each other. Two operators $A$ and $B$ commute if $AB = BA$.

### Key Concepts

- **Commutation**: Two operators $A$ and $B$ commute if $AB = BA$, or equivalently, if their commutator $[A, B] = AB - BA = 0$.
- **Abelian Group**: A group where all elements commute with each other.
- **Simultaneous Diagonalization**: A set of commuting Hermitian matrices can be simultaneously diagonalized, meaning there exists a common eigenbasis.
- **Commutant**: The set of all operators that commute with a given set of operators.

### Mathematical Properties of Abelian Sets

1. **Closure**: If $A$ and $B$ are in an Abelian set, then $AB$ is also in the set.
2. **Simultaneous Eigenvectors**: If $A$ and $B$ commute, they share a common set of eigenvectors.
3. **Function Composition**: If $f(A)$ and $g(B)$ are functions of commuting operators $A$ and $B$, then $f(A)g(B) = g(B)f(A)$.
4. **Exponential Property**: If $A$ and $B$ commute, then $e^{A+B} = e^A e^B$.

### Significance in Quantum Computing

1. **Compatible Observables**: In quantum mechanics, observables (represented by Hermitian operators) are compatible if they can be measured simultaneously with arbitrary precision. This happens if and only if they commute.

2. **Stabilizer Formalism**: In quantum error correction, stabilizer codes are defined using an Abelian subgroup of the Pauli group. The code space is the common eigenspace of all stabilizer operators.

3. **Quantum Fourier Transform**: The quantum Fourier transform diagonalizes Abelian groups, which is crucial for algorithms like Shor's algorithm.

4. **Heisenberg Uncertainty Principle**: Non-commuting observables (like position and momentum) cannot be measured simultaneously with arbitrary precision, leading to the uncertainty principle.

### Commuting vs. Non-commuting Operators

Consider the Pauli matrices $X$, $Y$, and $Z$:

1. Non-commuting example:
   $$XZ = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}\begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix} = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}$$
   
   $$ZX = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}\begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}$$
   
   Since $XZ \neq ZX$, these operators do not commute and form a non-Abelian set.

2. Commuting example:
   Consider the operators $Z_1 = Z \otimes I$ and $Z_2 = I \otimes Z$ (Z operators acting on the first and second qubits of a two-qubit system, respectively):
   
   $$Z_1 Z_2 = (Z \otimes I)(I \otimes Z) = Z \otimes Z = Z_2 Z_1$$
   
   Since $Z_1 Z_2 = Z_2 Z_1$, these operators commute and form an Abelian set.

### Abelian Sets in Stabilizer Codes

In quantum error correction, stabilizer codes use Abelian subgroups of the Pauli group. For example, the three-qubit bit-flip code has stabilizers:
- $Z_1 Z_2 = Z \otimes Z \otimes I$
- $Z_2 Z_3 = I \otimes Z \otimes Z$

These operators commute, so they form an Abelian set. The code space is the common +1 eigenspace of these operators.

## Tensor Products

Tensor products are a fundamental operation in quantum computing, used to describe composite quantum systems made up of multiple qubits.

### Key Concepts

- **Tensor Product**: An operation that combines two vector spaces to form a larger vector space. Denoted by $\otimes$.
- **Dimensions**: If $V$ is an $m$-dimensional space and $W$ is an $n$-dimensional space, then $V \otimes W$ is an $m \times n$-dimensional space.
- **Basis**: If $\{|v_i\rangle\}$ is a basis for $V$ and $\{|w_j\rangle\}$ is a basis for $W$, then $\{|v_i\rangle \otimes |w_j\rangle\}$ is a basis for $V \otimes W$.
- **Separable States**: States that can be written as tensor products of individual subsystem states.
- **Entangled States**: States that cannot be written as tensor products of individual subsystem states.

### Tensor Product of Vectors

For vectors $|v\rangle = \begin{pmatrix} a \\ b \end{pmatrix}$ and $|w\rangle = \begin{pmatrix} c \\ d \end{pmatrix}$, their tensor product is:

$$|v\rangle \otimes |w\rangle = \begin{pmatrix} a \\ b \end{pmatrix} \otimes \begin{pmatrix} c \\ d \end{pmatrix} = \begin{pmatrix} ac \\ ad \\ bc \\ bd \end{pmatrix}$$

### Tensor Product of Matrices

For matrices $A$ and $B$, their tensor product $A \otimes B$ is:

$$A \otimes B = \begin{pmatrix} a_{11}B & a_{12}B & \cdots \\ a_{21}B & a_{22}B & \cdots \\ \vdots & \vdots & \ddots \end{pmatrix}$$

For example, if $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$ and $B = \begin{pmatrix} e & f \\ g & h \end{pmatrix}$, then:

$$A \otimes B = \begin{pmatrix} ae & af & be & bf \\ ag & ah & bg & bh \\ ce & cf & de & df \\ cg & ch & dg & dh \end{pmatrix}$$

### Properties of Tensor Products

1. **Bilinearity**: $(a|v_1\rangle + b|v_2\rangle) \otimes |w\rangle = a(|v_1\rangle \otimes |w\rangle) + b(|v_2\rangle \otimes |w\rangle)$
2. **Associativity**: $(A \otimes B) \otimes C = A \otimes (B \otimes C)$
3. **Distributivity over Addition**: $A \otimes (B + C) = A \otimes B + A \otimes C$
4. **Compatibility with Matrix Multiplication**: $(A \otimes B)(C \otimes D) = (AC) \otimes (BD)$
5. **Trace Property**: $\text{Tr}(A \otimes B) = \text{Tr}(A) \cdot \text{Tr}(B)$
6. **Determinant Property**: $\det(A \otimes B) = \det(A)^{\dim(B)} \cdot \det(B)^{\dim(A)}$
7. **Kronecker Mixed-Product Property**: $(A \otimes B)(C \otimes D) = (AC) \otimes (BD)$
8. **Transpose Property**: $(A \otimes B)^T = A^T \otimes B^T$
9. **Conjugate Transpose Property**: $(A \otimes B)^\dagger = A^\dagger \otimes B^\dagger$

### Multi-Qubit States

1. **Two-Qubit Basis States**:
   - $|00\rangle = |0\rangle \otimes |0\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix} \otimes \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 1 \\ 0 \\ 0 \\ 0 \end{pmatrix}$
   - $|01\rangle = |0\rangle \otimes |1\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix} \otimes \begin{pmatrix} 0 \\ 1 \end{pmatrix} = \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix}$
   - $|10\rangle = |1\rangle \otimes |0\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix} \otimes \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 1 \\ 0 \end{pmatrix}$
   - $|11\rangle = |1\rangle \otimes |1\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix} \otimes \begin{pmatrix} 0 \\ 1 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 1 \end{pmatrix}$

2. **Separable vs. Entangled States**:
   - Separable state: $|\psi\rangle = |0\rangle \otimes |+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |01\rangle)$
   - Entangled state: $|\Phi^+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$

### Bell States

The Bell states are maximally entangled two-qubit states:

1. $|\Phi^+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$
2. $|\Phi^-\rangle = \frac{1}{\sqrt{2}}(|00\rangle - |11\rangle)$
3. $|\Psi^+\rangle = \frac{1}{\sqrt{2}}(|01\rangle + |10\rangle)$
4. $|\Psi^-\rangle = \frac{1}{\sqrt{2}}(|01\rangle - |10\rangle)$

These states are important in quantum teleportation, superdense coding, and quantum key distribution.

### Tensor Products in Quantum Gates

Multi-qubit gates can be constructed using tensor products:

1. **Controlled-NOT (CNOT) Gate**:
   $$\text{CNOT} = |0\rangle\langle 0| \otimes I + |1\rangle\langle 1| \otimes X = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}$$

2. **Single-Qubit Gate on a Multi-Qubit System**:
   - $X \otimes I$ applies the X gate to the first qubit and leaves the second qubit unchanged
   - $I \otimes Z$ applies the Z gate to the second qubit and leaves the first qubit unchanged

3. **SWAP Gate**:
   $$\text{SWAP} = \sum_{i,j} |i\rangle\langle j| \otimes |j\rangle\langle i| = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}$$

### Partial Trace

The partial trace is an operation that allows us to obtain the density matrix of a subsystem from the density matrix of the composite system.

For a bipartite system with density matrix $\rho_{AB}$, the partial trace over system B is:

$$\rho_A = \text{Tr}_B(\rho_{AB}) = \sum_i (I_A \otimes \langle i|_B) \rho_{AB} (I_A \otimes |i\rangle_B)$$

where $\{|i\rangle_B\}$ is an orthonormal basis for system B.

The partial trace is important for describing the state of a subsystem when the composite system is in an entangled state.

## Quantum Circuits and Linear Algebra

Quantum circuits provide a way to visualize and design quantum algorithms. Each quantum circuit corresponds to a sequence of linear transformations applied to quantum states.

### Quantum Circuit Elements

1. **Qubits**: Represented as horizontal lines in a circuit diagram.
2. **Single-Qubit Gates**: Represented as boxes on a single qubit line.
3. **Multi-Qubit Gates**: Represented as boxes spanning multiple qubit lines.
4. **Measurements**: Represented by meters at the end of qubit lines.

### Single-Qubit Gates as Linear Transformations

Single-qubit gates are represented by 2×2 unitary matrices:

1. **Hadamard Gate (H)**:
   $$H = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$$
   Creates superpositions: $H|0\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)$

2. **Phase Gate (S)**:
   $$S = \begin{pmatrix} 1 & 0 \\ 0 & i \end{pmatrix}$$
   Adds a π/2 phase to the $|1\rangle$ component.

3. **T Gate**:
   $$T = \begin{pmatrix} 1 & 0 \\ 0 & e^{i\pi/4} \end{pmatrix}$$
   Adds a π/4 phase to the $|1\rangle$ component.

4. **Rotation Gates**:
   - $R_x(\theta)$: Rotation around the x-axis of the Bloch sphere
   - $R_y(\theta)$: Rotation around the y-axis of the Bloch sphere
   - $R_z(\theta)$: Rotation around the z-axis of the Bloch sphere

### Multi-Qubit Gates as Linear Transformations

Multi-qubit gates are represented by larger unitary matrices:

1. **CNOT Gate**:
   $$\text{CNOT} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}$$
   Flips the target qubit if the control qubit is $|1\rangle$.

2. **Toffoli Gate (CCNOT)**:
   An 8×8 matrix that flips the target qubit if both control qubits are $|1\rangle$.

3. **SWAP Gate**:
   $$\text{SWAP} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}$$
   Swaps the states of two qubits.

### Universal Gate Sets

A set of quantum gates is universal if any unitary operation can be approximated to arbitrary precision using only gates from that set. Examples include:

1. **Clifford + T**: The Clifford group (generated by H, S, and CNOT) plus the T gate
2. **Rotation Gates + CNOT**: Arbitrary single-qubit rotations plus the CNOT gate

### Circuit Identities

Quantum circuit identities are equations showing equivalent combinations of gates:

1. **Double Negation**: $XX = I$, $YY = I$, $ZZ = I$
2. **Hadamard Identities**: $HXH = Z$, $HYH = -Y$, $HZH = X$
3. **CNOT Identities**: CNOT can be expressed as $|0\rangle\langle 0| \otimes I + |1\rangle\langle 1| \otimes X$

### Matrix Multiplication and Circuit Composition

When gates are applied in sequence, their effect is represented by matrix multiplication:

1. **Sequential Gates**: If gate $U$ is applied followed by gate $V$, the combined effect is $VU$.
2. **Parallel Gates**: If gate $U$ is applied to one qubit and gate $V$ to another, the combined effect is $U \otimes V$.

### Example: Quantum Teleportation Circuit

The quantum teleportation circuit can be analyzed using linear algebra:

1. **Initial State**: $|\psi\rangle \otimes |00\rangle$
2. **After Bell State Preparation**: $|\psi\rangle \otimes \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$
3. **After CNOT and H on the first qubit**: A state that encodes $|\psi\rangle$ in entanglement
4. **After Measurement and Classical Communication**: The third qubit is in state $|\psi\rangle$ after appropriate corrections

This demonstrates how quantum circuits can be analyzed using the linear algebraic formalism of quantum mechanics.
