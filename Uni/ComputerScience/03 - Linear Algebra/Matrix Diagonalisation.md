Matrix diagonalisation is the process of performing a similarity transformation on a matrix in order to recover a [[Special Types of Matrices#Similar Matrices|similar matrix]] which is [[Special Types of Matrices#Diagonal Matrix|diagonal]]. Once a matrix is diagonalised it is very easy to raise it to integer powers. Not all matrices are diagonalisable. 

# Diagonalisable Matrices
Let A be a k x k matrix. We say that A is diagonalisable if and only if it is similar to a diagonal matrix. A is diagonal is there exists an invertible matrix P such that $D=P^-1 AP$ where D is a diagonal matrix.

# Process
In order to diagonalise a matrix A:
1. Compute the eigenvalues of A
2. Check that no eigenvalue is defective (its algebraic multiplicity is higher than its geometric multiplicity). Defective eigenvalues don't work since it means that there isn't a complete set of linearly independent eigenvectors.
3. For each eigenvalue, find as many linearly independent eigenvectors as possible.
4. Adjoin all the eigenvectors so as to form a full-rank matrix P
5. Build a diagonal matrix D whose diagonal elements are the eigenvalues of A
6. The diagonalisation is done $D=P^-1 AP$

## Example
# Matrix Diagonalisation Example

Let  
$$
A = \begin{bmatrix}
4 & 1 \\
2 & 3
\end{bmatrix}
$$

We aim to diagonalise \( A \), i.e., find an invertible matrix \( P \) and a diagonal matrix \( D \) such that:

$$
A = P D P^{-1}
$$

---

## Step 1: Find the Eigenvalues

Compute the characteristic polynomial:

$$
\det(A - \lambda I) = 
\begin{vmatrix}
4 - \lambda & 1 \\
2 & 3 - \lambda
\end{vmatrix}
= (4 - \lambda)(3 - \lambda) - 2
= \lambda^2 - 7\lambda + 10
$$

Solve:

$$
\lambda^2 - 7\lambda + 10 = 0 \quad \Rightarrow \quad (\lambda - 5)(\lambda - 2) = 0
$$

So the eigenvalues are:  
$\lambda_1 = 5, \quad \lambda_2 = 2$ 

---
### Step 2: Eigenvector for $\lambda = 5$

We compute the matrix \( A - 5I \):

$$
A - 5I = 
\begin{bmatrix}
4 - 5 & 1 \\
2 & 3 - 5
\end{bmatrix}
=
\begin{bmatrix}
-1 & 1 \\
2 & -2
\end{bmatrix}
$$

Now we solve the equation:

$$
(A - 5I) \vec{v} = \vec{0}
$$

Let $\vec{v} = \begin{bmatrix}x \\ y\end{bmatrix}$. Then:

$$
\begin{bmatrix}
-1 & 1 \\
2 & -2
\end{bmatrix}
\begin{bmatrix}
x \\
y
\end{bmatrix}
=
\begin{bmatrix}
-x + y \\
2x - 2y
\end{bmatrix}
=
\begin{bmatrix}
0 \\
0
\end{bmatrix}
$$

This gives the equations:

$$
-x + y = 0 \quad \Rightarrow \quad x = y
$$

So the general solution (eigenvector) is:

$$
\vec{v}_1 = 
y \begin{bmatrix}
1 \\
1
\end{bmatrix}
$$

We can choose \( y = 1 \) for simplicity, giving:

$$
\vec{v}_1 = \begin{bmatrix}1 \\ 1\end{bmatrix}
$$

This is the eigenvector corresponding to $\lambda = 5$.

---
###  Step 3: Eigenvector for $\lambda = 2$

We compute the matrix \( A - 2I \):

$$
A - 2I = 
\begin{bmatrix}
4 - 2 & 1 \\
2 & 3 - 2
\end{bmatrix}
= 
\begin{bmatrix}
2 & 1 \\
2 & 1
\end{bmatrix}
$$

Now we solve the equation:

$$
(A - 2I) \vec{v} = \vec{0}
$$

Let $\vec{v} = \begin{bmatrix}x \\ y\end{bmatrix}$. Then:

$$
\begin{bmatrix}
2 & 1 \\
2 & 1
\end{bmatrix}
\begin{bmatrix}
x \\
y
\end{bmatrix}
=
\begin{bmatrix}
2x + y \\
2x + y
\end{bmatrix}
=
\begin{bmatrix}
0 \\
0
\end{bmatrix}
$$

This gives the equation:

$$
2x + y = 0 \quad \Rightarrow \quad x = -\frac{1}{2}y
$$

So the general solution (eigenvector) is:

$$
\vec{v}_2 = 
y \begin{bmatrix}
-1/2 \\
1
\end{bmatrix}
$$

To simplify, we multiply by 2 (any non-zero scalar works), giving:

$$
\vec{v}_2 = \begin{bmatrix}-1 \\ 2\end{bmatrix}
$$

This is the eigenvector corresponding to $\lambda = 2$.

---

## Step 4: Form P and D

Matrix of eigenvectors:

$$
P = \begin{bmatrix}
1 & -1 \\
1 & 2
\end{bmatrix}
$$

Diagonal matrix of eigenvalues:

$$
D = \begin{bmatrix}
5 & 0 \\
0 & 2
\end{bmatrix}
$$

---

## Step 5: Verify $A = P D P^{-1}$

Calculate $P^{-1}$ and confirm that:
$$
A = P D P^{-1}
$$


