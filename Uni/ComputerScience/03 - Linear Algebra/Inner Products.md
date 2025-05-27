The inner product of two vectors $\mathbf{u}$ and $\mathbf{v}$, $\langle \mathbf{u}, \mathbf{v} \rangle$ is a function that associates each pair $\mathbf{u}, \mathbf{v}$ in to a real number $\langle \mathbf{u}, \mathbf{v} \rangle$ in $\mathbb{R}^n$ , satisfying the following properties for all $\mathbf{u}$, $\mathbf{v}$, $\mathbf{w}$  $\in$ $V$ and $k \in \mathbb{R}^n$::
- $\langle \mathbf{u}, \mathbf{v} \rangle$ = $\langle \mathbf{v}, \mathbf{u} \rangle$ (Symmetry axiom)
- $\langle \mathbf{u}, \mathbf{v} + \mathbf{w} \rangle =  \langle \mathbf{u}, \mathbf{w} \rangle + \langle \mathbf{v}, \mathbf{w} \rangle$ (Additivity)
- $\langle k\mathbf{u}, \mathbf{v} \rangle = k\langle \mathbf{u}, \mathbf{v} \rangle$ (Homogeneity axiom)
- $\langle \mathbf{v}, \mathbf{v} \rangle \geq 0$ and $\langle \mathbf{v}, \mathbf{v} \rangle$ iff $\mathbf{v} = 0$ (Positivity Axiom)

# Norm and Distance

- $||\mathbf{v}||$  = $\sqrt{\langle \mathbf{v}, \mathbf{v} \rangle}$   
- Orthogonality: Vectors $\mathbf{v}$ and $\mathbf{u}$ are orthogonal if $\langle \mathbf{u}, \mathbf{v} \rangle = 0$
- Unit vector: Vector with norm 1.
- Orthogonal complement( $W^\perp$): Set of vectors orthogonal to every vector in subspace $W$
- Orthonormality: Vectors $\mathbf{v}$ and $\mathbf{u}$ are orthogonal unit vectors.
# Examples of Inner Products
--- 
## Dot Product
For vectors $u=(u_1​,u_2​,…,u_n​)$ and $v=(v_1,v_2,…,v_n)$:
$$⟨u,v⟩=u_1v_1+u_2v_2+⋯+u_nv_n=∑_{i=1}^n{u_iv_i}$$

---
## Weighted Euclidean Inner Product
Given positive weights $w_1,w_2,...,w_n \in \mathbb{R}$
$$\langle \mathbf{u},\mathbf{v} \rangle = ∑_{i=1}^n{w_iu_iv_i}$$
---
## Matrix Inner Product

Let $( A \in \mathbb{R}^{n \times n})$ be invertible. Define:

$$
\langle u, v \rangle = (Au)^T (Av) = u^T A^T A v
$$

This defines an inner product on $\mathbb{R}^n$ induced by matrix $A$.

---

## Standard Inner Product on $P^n$

Let $p(x) = \sum_{i=0}^n a_i x^i, q(x) = \sum_{i=0}^n b_i x^i$. Define:

$$
\langle p, q \rangle = \sum_{i=0}^n a_i b_i
$$

This is the dot product on the coefficient vectors in $\mathbb{R}^{n+1}$.

---

## Evaluation Inner Product on $P^n$

Given distinct points $x_1, \dots, x_m \in \mathbb{R}$, define:

$$
\langle p, q \rangle = \sum_{i=1}^m p(x_i) q(x_i)
$$

Used in interpolation and discrete approximation contexts.

---

## Inner Product on $C[a, b]$

For continuous functions $f, g \in C[a, b]$, define:

$$
\langle f, g \rangle = \int_a^b f(x) g(x) \, dx
$$

This extends the dot product to infinite-dimensional function spaces.

---

## Complex Inner Product

For $u, v \in \mathbb{C}^n$, define:

$$
\langle u, v \rangle = \sum_{i=1}^n u_i \overline{v_i}
$$

The complex conjugate ensures $\langle v, v \rangle \geq 0$ and is real.

---


