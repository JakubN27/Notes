An orthogonal basis is a [[Linear Independence#Basis|basis]] set in which all distinct pairs of vectors are [[Inner Products|orthogonal]].
An orthonormal basis is like an orthogonal basis but all vectors are also unit vectors.
For example:
$$\Biggl\{ \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix} ,\begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix} ,\begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix} \Biggl\} \in \mathbb{R}^3$$

---
# Decomposition Theorem

Recall: Every vector in a vector space can be written as a linear combination of its bases.
Similarly, every vector can be written as a combination of orthogonal basis vectors.
Let $\{ v_1, v_2, \dots, v_n\}$ be a basis for a subspace $W \subseteq V$, and let $u \in W$.

---

### Orthogonal Basis Case

If the basis is **orthogonal**, then:

$$
u = \sum_{i=1}^n \frac{\langle u, v_i \rangle}{||v_i||} v_i
$$

Each term scales the direction $v_i$ by the projection of $u$ onto $v_i$.

---

### Orthonormal Basis Case

If the basis is **orthonormal**, then $\langle v_i, v_i \rangle = 1$, and the decomposition simplifies to:

$$
u = \sum_{i=1}^n \langle u, v_i \rangle v_i
$$

This makes the coefficients just the inner products (i.e., projections) of $u$ onto each basis vector.

---
## Projection Theorem

Any vector $\mathbf{u}$ in $V$ can be uniquely written as $\mathbf{u} = \mathbf{w_1} + \mathbf{w_2}, \mathbf{w_1} \in W, \mathbf{w_2} \in W^{\perp}$ 
