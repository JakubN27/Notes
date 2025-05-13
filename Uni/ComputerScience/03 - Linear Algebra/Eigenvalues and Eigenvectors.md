# Eigenvectors
An eigenvector (or characteristic vector) is vector that has its direction scaled (unchanged or reversed) by a linear transformation. It is scaled by a factor $\lambda$, when the linear transformation T is applied to the eigenvector v: $Tv=\lambda v$

# Eigenvalues
An eigenvalue is the scale factor applied to its corresponding eigenvector under the linear transformation T. When a matrix A represents the linear transformation T, an eigenvalue $\lambda$ will satisfy the following equations:
$$(A-\lambda I)v = 0$$
and subsequently:
$$det(A - \lambda I) = 0$$
this leads to a polynomial known as the characteristic polynomial :
$$det(A-\lambda I) = (\lambda_1 - \lambda)(\lambda_2 - \lambda)...(\lambda_n - \lambda)$$
where $\lambda_1 ... \lambda_n$ are the eigenvalues of A. These don't necessarily have distinct or positive values. 

## Some properties:
- The determinant of A is the product of all its eigenvalues. 
- A matrix A is invertible only if all eigenvalues are nonzero.
- If A is invertible, the eigenvalues of the inverse are the reciprocals of the original eigenvalues. The eigenvalues also share the same multiplicity
- Algebraic multiplicity is the number of times an eigenvalues appears as a solution to a characteristic polynomial.
- Geometric multiplicity is the number of linearly independent eigenvectors associated with an eigenvalue.
- Eigenvalues can have complex values with complex matrices and vector spaces.
- Eigenvalues and eigenvalues can be used for [[Matrix Diagonalisation]].
- When the algebraic multiplicity is the same as the geometric multiplicity, the matrix is diagonalisable.
# Eigenspace
The eigenspace is a subspace of a vector space consisting of all eigenvalues associated with a specific eigenvalue of a linear transformation or matrix, along with the zero vector. 
- A set of linearly independent eigenvectors form a basis for an eigenspace.
- The geometric multiplicity of an eigenvalue corresponds to the dimension of its eigenspace.