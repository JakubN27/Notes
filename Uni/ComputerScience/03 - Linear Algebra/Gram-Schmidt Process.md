The process is used to construct on orthogonal (or orthonormal) basis from any basis by iteratively subtracting projections to remove non orthogonal components of each vector.

To convert a (linearly independent) set S = {$\mathbf{u}_1, \mathbf{u}_2, \dots, \mathbf{u}_n$} into an orthogonal basis for span(S), do the following:
1) $\mathbf{v}_1 = \mathbf{u}_1$ 
2) $\mathbf{v}_2 = \mathbf{u}_2 - \frac{\langle \mathbf{u}_2, \mathbf{v}_1 \rangle}{||\mathbf{v}_1||^2} \mathbf{v}_1$
3) continue for n steps, subtracting projection from each vector in set.
4) Normalise all vectors if an orthonormal basis is needed.
