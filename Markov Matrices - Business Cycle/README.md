# Markov Matrices

## Introduction to Markov Chains

In a hypothetical country, every decade, $5$ percent of the rural population migrates to cities and $0.1$ percent of city dwellers migrate back to rural areas.

#### Exercise 1
Write the algebraic relation for the future population shares of cities ($c_{t+1}$) and rural areas ($v_{t+1}$) in terms of the current population shares of cities ($c_{t}$) and rural areas ($v_{t}$).

#### Exercise 2

Define the population distribution vector as

$$
p_t =
\begin{pmatrix}
c_t \\
v_t \\
\end{pmatrix}
$$

Rewrite the relation for $p_{t+1}$ in terms of a matrix multiplication.

#### Exercise 3

Assuming the vector $p_0$ represents the population distribution at the initial time and $p_t$ represents the population distribution after $t$ decades, what is the relation of $p_t$ in terms of $p_0$?

> #### Note:
> Matrices like the coefficient matrix in this problem, which are square and represent probabilities, are called **Markov Matrices**.

#### Exercise 4

Based on the concept of Markov matrices and the matrix properties you formed in the previous problem, which of the following matrices is a Markov matrix? Describe two properties of Markov matrices according to probability principles.

$$
A_1 =
\begin{bmatrix}
0.2 & 0.2 & 0.6 \\
0.3 & 0.5 & 0.2 \\
0.5 & 0.2 & 0.3 \\
\end{bmatrix}
\quad
A_2 =
\begin{bmatrix}
-0.1 & 0 & 0.2 \\
0.4 & 0.8 & 1.2 \\
0.7 & 0.2 & -0.4 \\
\end{bmatrix}
\quad
A_3 =
\begin{bmatrix}
0.25 & 0.3 & 0.1 \\
0.1 & 0.5 & 0 \\
0.65 & 0.2 & 0.9 \\
\end{bmatrix}
$$

#### Exercise 5

Given the two properties of Markov matrices, show that:

a) Every Markov matrix has an eigenvalue equal to 1.

b) The eigenvalues of a Markov matrix are not greater than 1. 
*Hint: For which entry of $A^T v$ cannot be greater than the entry of $v$?*

> #### Definition
> A **Stochastic Vector** represents a discrete probability distribution with non-negative entries that sum to 1. Each entry of this vector represents the probability of one of the possible outcomes in a conventional ordering.

The figure below shows a **Markov Chain** with two states. The initial probability of being in each state is denoted by the probability vector $p_0$, known as the initial state distribution. In a Markov Chain, the transition probability to each state depends only on the current state. Thus, the chain can be described with a 2x2 Markov matrix, similar to Question 1.

![Markov Chain](images/markov-chain.jpg)

Here, a more formal definition for the probability vector and transition matrix, which is a Markov matrix, is provided:

```math
p_t =
\begin{pmatrix}
Pr\{S_t=1\} \\
Pr\{S_t=2\} \\
\end{pmatrix}
A =
\begin{bmatrix}
Pr\{S_t=1 | S_{t-1}=1\} & Pr\{S_t=1 | S_{t-1}=2\} \\ 
Pr\{S_t=2 | S_{t-1}=1\} & Pr\{S_t=2 | S_{t-1}=2\} \\
\end{bmatrix}
=
\begin{bmatrix}
1-\alpha & \beta \\ 
\alpha & 1-\beta \\
\end{bmatrix}
```

If the initial state distribution is given as

$$
p_0 =
\begin{pmatrix}
0.3 \\
0.7 \\
\end{pmatrix}
$$

this means that initially, there is a $0.3$ probability of being in state $S_1$ and a $0.7$ probability of being in state $S_2$. This probability distribution changes to $p_1 = A p_t$ in the next moment, representing the probability of being in each state at the next moment.

An optional study of this [interactive booklet](https://setosa.io/ev/markov-chains/) may help in understanding the concept of Markov chains.

## Introduction to Numerical Methods

#### Exercise 6

For the matrix 

$$
A =
\begin{bmatrix}
0.6 & 0.5 \\ 
0.1 & 1 \\
\end{bmatrix}
$$

plot the vectors $v, Av, A^2v, A^3v, \ldots, A^{10}v$ for three values of 

$$
v_1 =
\begin{pmatrix}
1 \\ 
0.5 \\
\end{pmatrix}
\quad
v_2 =
\begin{pmatrix}
-2 \\ 
1 \\
\end{pmatrix}
\quad
v_3 =
\begin{pmatrix}
2 \\ 
-1 \\
\end{pmatrix}
$$

in separate plots. Also, find the eigenvalues and eigenvectors of this matrix using built-in functions, and show the direction of the eigenvectors as lines on these plots.

Based on the plots, what direction does $A^N v$ tend towards as $N$ increases?

#### Exercise 7

Explain the observed behavior in the previous question by decomposing a hypothetical vector $v$ along the eigenvectors and find an exceptional case.

#### Exercise 8

Based on the result from the previous question, suggest a method to find an eigenvector and eigenvalue of a matrix using iterative matrix multiplication. Which eigenvalue and eigenvector does this method find? Write a function that, given a matrix and the number of iterations as input, finds and returns the corresponding eigenvector and eigenvalue using the suggested method. Test your function and compare the results with built-in functions.

> #### Note:
> Your function should not suffer from numerical instability for very large or small numbers of iterations or eigenvalues.

#### Exercise 9

Given the set of eigenvalues $\{\lambda_1, \ldots, \lambda_n \}$ and eigenvectors $\{ v_1, \ldots, v_n \}$ of matrix $A$, infer the eigenvalues and eigenvectors of matrix $A - \mu I$.

#### Exercise 10

Investigate the inverse iteration method, which is a technique for finding eigenvalues and eigenvectors of a matrix, and explain its logic. Implement this method in a function with the assumption that a shift value is provided as input. How does this method overcome the limitation of the power iteration method?

#### Exercise 11

If we have a biased coin and do not know the probability of heads or tails, how can we determine this probability? How can the accuracy of this method be improved?

#### Exercise 12

In cases where the formulation of a probabilistic problem is complex or some values are unknown, the **Monte Carlo Estimation** method can be useful for obtaining certain variables through experiments and sampling. Briefly explain the use of this method in estimating the value of $\pi$ based on this [interactive booklet](https://observablehq.com/@jajoosam/mathe-carlo/2).

#### Exercise 13

In a Markov chain, the steady state distribution is a vector to which the probability distribution vector tends as $t \to \infty$. Based on what you learned from the Monte Carlo method, suggest a method to estimate the steady state distribution in a Markov chain using simulation and sampling.

> #### Note:
> The proposed method should not use matrix multiplication and should only rely on sampling from probability distributions.
