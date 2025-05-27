## Definition
Let $A$ be an $m \times n$ matrix with **linearly independent columns** $u_1, \ldots, u_n$. The QR decomposition factors $A$ as:
$$
A = QR
$$
where:
- $Q$ is an $m \times n$ matrix with **orthonormal columns** (from Gram-Schmidt)
- $R$ is an $n \times n$ **invertible upper triangular** matrix
---
## Construction via Gram-Schmidt
1. Apply Gram-Schmidt to columns $\{u_1, \ldots, u_n\}$ to get orthonormal $\{q_1, \ldots, q_n\}$
2. Express original columns in the new basis:
   $$
   \begin{aligned}
   u_1 &= \langle u_1, q_1 \rangle q_1 \\
   u_2 &= \langle u_2, q_1 \rangle q_1 + \langle u_2, q_2 \rangle q_2 \\
   &\vdots \\
   u_n &= \sum_{k=1}^n \langle u_n, q_k \rangle q_k
   \end{aligned}
   $$
3. Form matrices:
   - $Q = [q_1 | \cdots | q_n]$
   - $R$ contains coefficients $\langle u_i, q_j \rangle$:
$$
     R = \begin{pmatrix}
     \langle u_1, q_1 \rangle & \langle u_2, q_1 \rangle & \cdots & \langle u_n, q_1 \rangle \\
     0 & \langle u_2, q_2 \rangle & \cdots & \langle u_n, q_2 \rangle \\
     \vdots & \vdots & \ddots & \vdots \\
     0 & 0 & \cdots & \langle u_n, q_n \rangle
     \end{pmatrix}
     $$
---
## Key Properties
- **Triangularity**: $R$ is upper triangular because $q_j \perp u_i$ for $i < j$ (Gram-Schmidt property)
- **Positive Diagonal**: $\langle u_i, q_i \rangle > 0$ (since $\langle v_i, v_i \rangle > 0$ in Gram-Schmidt)
- **Uniqueness**: When $A$ has full column rank, the decomposition is unique if we require positive diagonal entries in $R$

## Example
For matrix $A = \begin{pmatrix}1&1&1\\0&1&1\\0&0&1\end{pmatrix}$:
1. Gram-Schmidt gives:
   $$
   q_1 = \begin{pmatrix}1\\0\\0\end{pmatrix},\ 
   q_2 = \begin{pmatrix}0\\1\\0\end{pmatrix},\ 
   q_3 = \begin{pmatrix}0\\0\\1\end{pmatrix}
   $$
2. Compute $R$ entries:
   $$
   R = \begin{pmatrix}
   1 & 1 & 1 \\
   0 & 1 & 1 \\
   0 & 0 & 1
   \end{pmatrix}
   $$
3. Thus $A = QR$ with $Q = I_3$ in this case.

---
## Applications

- [[Least Squares Approximation]]: Solves $A^TAx = A^Tb$ more stably via $Rx = Q^Tb$
- **Eigenvalue Algorithms**: Used in the QR algorithm for computing eigenvalues
- **Orthogonalisation**: Basis for many numerical linear algebra methods

> **Theorem**: Every full-rank matrix has a unique QR decomposition with positive diagonal entries in $R$.

## Supplemental: When is $R$ Invertible?
$R$ is invertible $\iff$ $A$ has linearly independent columns $\iff$ $A^TA$ is invertible.

