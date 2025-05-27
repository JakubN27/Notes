Assume you want to determine, possibly approximately, the quantitative dependency between two parameters x and y in some process. You want a line of best fit for some set of points $\{(x_1,y_1, \dots, (x_n,y_n) \}$ . This method works for a simple straight line y = a +bx and more complex curves.
This can be written as a set of equations
$$a +bx_1 = y_1$$
$$\vdots$$
$$a+bx_n = y_n$$
Or in matrix form:
$$\begin{pmatrix} 1 & x_1\\ \vdots & \vdots\\ 1 & x_n\end{pmatrix} \begin{pmatrix} a\\b\end{pmatrix} = \begin{pmatrix} y_1\\ \vdots\\y_n\end{pmatrix}$$
We need to find a least squares solution to the system Av = y. If matrix A has linearly independent columns, then the solution is simple using the [[Least Squares Approximation]], we will turn this into the normal system: 
$$A^TAx=A^Tb \implies x=(A^TA)^{−1}A^Tb$$
This will yield unique solutions. For any m x n matrix, A has linearly independent columns if $A^TA$ is invertible.

---

In the case that it isn't, we need to use [[QR Decomposition]] to break down A into QR. 
Where:
- $Q \in \mathbb{R}^{m*n}$ has orthonormal columns: $Q^TQ = I$ 
- $R \in \mathbb{R}^{n*n}$ is upper trianguler.
Replace A with QR:
$$
\| QR \vec{x} - \vec{b} \|
$$

Multiply both sides by $Q^T$ $ to simplify:
$$
Q^T QR \vec{x} = Q^T \vec{b}
$$

Since $Q^TQ=I$, this reduces to:
$$
R \vec{x} = Q^T \vec{b}
$$Solve:
$$
R \vec{x} = Q^T \vec{b}
$$

This is a standard **upper triangular system**, which can be solved via **back-substitution**.

---