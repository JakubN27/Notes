Matrices with certain properties can be useful for identifying properties or easier operations.

# Square Matrix
A square matrix has the same number of rows and columns
$$\begin{bmatrix}  
a_{11} & a_{12} & a_{13}\\  
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33}
\end{bmatrix}$$
# Diagonal Matrix
A diagonal matrix is one where all non zero entries are only on the main diagonal of the matrix.
For example:

$$\begin{bmatrix}  
a_{11} & a_{12} & a_{13}\\  
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33}
\end{bmatrix}$$
# Triangular Matrix
A triangular matrix is one where all zero entries are on the main diagonal and all above or below it. For example:
$$\begin{bmatrix}  
a_{11} & a_{12} & a_{13}\\  
0 & a_{22} & a_{23} \\
0 & 0 & a_{33}
\end{bmatrix} or  \begin{bmatrix}  
a_{11} & 0 & 0\\  
a_{21} & a_{22} & 0 \\
a_{31} & a_{32} & a_{33}
\end{bmatrix}$$
# Symmetric Matrix
A symmetric matrix is a square matrix which is equal to its transpose (reflected along its main diagonal). For example:
$$\begin{bmatrix}  
a_{11} & a_{12} & a_{13}\\  
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33}
\end{bmatrix} = \begin{bmatrix}  
a_{11} & a_{21} & a_{31}\\  
a_{12} & a_{22} & a_{32} \\
a_{13} & a_{23} & a_{33}
\end{bmatrix} $$
# Orthogonal Matrix
A matrix whose inverse is equal to its transpose. i.e $A^{-1}=A^T$.
The columns (and rows) of an orthogonal matrix are orthonormal. This means they are mutually orthogonal (perpendicular) and have a modulus of 1. The determinant of an orthogonal matrix is either 1 or -1. 

# Similar Matrices 
Two square matrices, A and B for instance, represent the same linear map under two possibly different bases. A and B are considered similar if there exists an invertible matrix P such that $B = P^-1 AP$. Similar matrices share the same eigenvalues, the same trace, same characteristic polynomial, and rank. 