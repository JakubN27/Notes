For any [[Special Types of Matrices#Orthogonal Matrix|orthogonal matrix]], the rows of it will form an orthonormal bases, and the columns will form another orthonormal basis. The determinant is always 1 or -1. Because of this we also know $||Q\mathbf{x}|| = ||\mathbf{x}||$ for all $\mathbf{x}$ in $\mathbb{R}^n$, and $⟨Qx, Qy⟩ = ⟨x, y⟩$ for all $\mathbf{x}$ and $\mathbf{y} \in \mathbb{R}^n$   

Recall: If A and B are [[Special Types of Matrices#Similar Matrices|similar]] then there is an invertible matrix P such that $P^{-1}AP = B$ .
If B above can be chosen to be diagonal then we say that A is diagonalisable and that P diagonalises A. If, in addition, P can be chosen to be orthogonal then we can say that A and B are orthogonally similar and that A is orthogonally diagonalisable and that P orthogonally diagonalises A (and then $P^TAP = B$ since $P^T = P^{-1}$)

---
# Orthogonal Diagonalisation
For any n x n matrix A the following are equivalent:
- A is orthogonally diagonalisable: $A = QDQ^T$ 
- A has an orthonormal basis of eigenvectors
- A is symmetric.

A has n real eigenvalues, even in complex vector spaces, and eigenvectors from different eigenspace are orthogonal.

To orthogonally diagonalise a symmetric:
1) Find the eigenvalues and a basis in each eigenspace of A.
2) Apply the [[Gram-Schmidt Process]] to each basis to obtain an orthonormal basis for each eigenspace. 
3) Form the matrix Q whose columns are the vectors found in Step 2. Q will orthogonally diagonalise A and the diagonal of D = $Q^TAQ$ contains the eigenvalues of A in the same order as eigenvectors in Q.
Essentially the same as normal diagonalisation but apply GSP to eigenvectors.

---
# Spectral Decomposition 

## Core Definition
Let $A$ be a **symmetric** $n \times n$ matrix with:
- Orthonormal eigenvectors: $\{u_1, \ldots, u_n\}$  
- Corresponding eigenvalues: $\{\lambda_1, \ldots, \lambda_n\}$

### Matrix Form
$$
A = QDQ^T = \underbrace{(u_1 | \ldots | u_n)}_{Q} 
\underbrace{\begin{pmatrix}
\lambda_1 & & 0 \\
& \ddots & \\
0 & & \lambda_n
\end{pmatrix}}_{D}
\underbrace{\begin{pmatrix}
u_1^T \\
\vdots \\
u_n^T
\end{pmatrix}}_{Q^T}
$$

### Projection Form (Spectral Theorem)
$$
A = \sum_{j=1}^n \lambda_j u_j u_j^T = \lambda_1 u_1 u_1^T + \cdots + \lambda_n u_n u_n^T
$$

## Key Properties
1. **Symmetry Requirement**: Only works for $A^T = A$
2. **Rank-1 Projections**: Each $u_j u_j^T$ is a rank-1 projection matrix
3. **Orthogonality**: $u_i^T u_j = \delta_{ij}$ guarantees diagonalisation