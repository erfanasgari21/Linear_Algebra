# Markov Matrices
## Introduction to Markov Chains

In a hypothetical country, each decade:
- 5% of villagers migrate to cities.
- 0.1% of city dwellers migrate back to villages.

#### 1. Write the algebraic relation for the population shares of cities, \(c_{t+1}\), and villages, \(v_{t+1}\), based on the current population shares of cities, \(c_t\), and villages, \(v_t\).

#### 2. Define the population distribution vector as:

$$
p_t = \begin{pmatrix} c_t \\ v_t \end{pmatrix}
$$

Rewrite the relation for \(p_{t+1}\) in matrix multiplication form.

### 3. Assuming \(p_0\) represents the population distribution at an initial time and \(p_t\) represents the population distribution after \(t\) decades, express \(p_t\) in terms of \(p_0\).

\begin{definition}
A **Markov matrix** is a square matrix that represents probabilities.
\end{definition}

### 4. Considering the Markov matrix properties, which of the following matrices are valid Markov matrices? State two key features of Markov matrices based on probability principles.
\[
A_1 = \begin{bmatrix} 0.2 & 0.2 & 0.6 \\ 0.3 & 0.5 & 0.2 \\ 0.5 & 0.2 & 0.3 \end{bmatrix}, \quad
A_2 = \begin{bmatrix} -0.1 & 0 & 0.2 \\ 0.4 & 0.8 & 1.2 \\ 0.7 & 0.2 & -0.4 \end{bmatrix}, \quad
A_3 = \begin{bmatrix} 0.25 & 0.3 & 0.1 \\ 0.1 & 0.5 & 0 \\ 0.65 & 0.2 & 0.9 \end{bmatrix}
\]

### 5. Based on the properties of Markov matrices:
- a) Prove that every Markov matrix has an eigenvalue of 1.
- b) Prove that the eigenvalues of a Markov matrix are less than or equal to 1.
*Hint: How can the entries of \(A^T v\) be larger than any entry of \(v\)?*

\begin{definition}
A **stochastic vector** represents a discrete probability distribution, where its entries are non-negative, and their sum is 1. Each entry corresponds to the probability of one of the possible outcomes.
\end{definition}

The following diagram represents a **Markov chain** with two states. The initial state distribution is represented by the vector \(p_0\), which describes the probability of being in each state. In a Markov chain, the transition probability to each state depends only on the current state, which can be represented by a 2x2 Markov matrix like the one in the following exercise.

\[
p_t = \begin{pmatrix} Pr\{S_t=1\} \\ Pr\{S_t=2\} \end{pmatrix}
\]
\[
A = \begin{bmatrix} Pr\{S_t=1|S_{t-1}=1\} & Pr\{S_t=1|S_{t-1}=2\} \\ Pr\{S_t=2|S_{t-1}=1\} & Pr\{S_t=2|S_{t-1}=2\} \end{bmatrix} = \begin{bmatrix} 1-\alpha & \beta \\ \alpha & 1-\beta \end{bmatrix}
\]

Assume the initial state distribution is:
\[
p_0 = \begin{pmatrix} 0.3 \\ 0.7 \end{pmatrix}
\]
This indicates that initially, there is a 30% chance of being in state \(S_1\) and a 70% chance of being in state \(S_2\). The distribution changes over time as \(p_1 = A p_t\), representing the probabilities of being in each state in the next time step.

Explore this [interactive tutorial](https://setosa.io/ev/markov-chains/) to gain more insights into Markov chains.

---

## SUBSECTION: Numerical Methods

### 6. [Implementation] For the matrix:
\[
A = \begin{bmatrix} 0.6 & 0.5 \\ 0.1 & 1 \end{bmatrix}
\]
Plot the vectors \(v, Av, A^2v, A^3v, \dots, A^{10}v\) for the following initial vectors:
\[
v_1 = \begin{pmatrix} 1 \\ 0.5 \end{pmatrix}, \quad v_2 = \begin{pmatrix} -2 \\ 1 \end{pmatrix}, \quad v_3 = \begin{pmatrix} 2 \\ -1 \end{pmatrix}
\]
Also, find the eigenvalues and eigenvectors of the matrix using built-in functions and show the eigenvector directions on the plot.

Based on the plots, to which direction does \(A^Nv\) converge as \(N\) increases?

### 7. Using eigenvector decomposition, explain the observed behavior in the previous question. Also, provide an example where this behavior does not hold.

### 8. [Implementation] Propose a method to find an eigenvector and eigenvalue of a matrix through repeated matrix multiplication. Which eigenvalue and eigenvector does this method find? Implement a function that takes a matrix and the number of iterations as input and returns the corresponding eigenvalue and eigenvector. Test your function and compare the results with built-in functions.

### 9. If \(\{\lambda_1, \dots, \lambda_n \}\) and \(\{ v_1, \dots, v_n \}\) are the eigenvalues and eigenvectors of matrix \(A\), find the eigenvalues and eigenvectors of matrix \(A - \mu I\).

### 10. [Implementation] Research the **Inverse Iteration Method** for finding eigenvalues and eigenvectors of a matrix. Implement this method in a function, assuming a shift value is provided as input. How does this method overcome the limitations of the power iteration method?
