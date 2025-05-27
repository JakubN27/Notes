# Stationary points

To find stationary points of a multivariate function, find all partial derivatives, or $\nabla f$ and set them equal to 0.
The corresponding values will be the stationary points.

---
# Testing for Maximum or Minimum
To test the stationary point of a multivariate function for a maximum, minimum, or a saddle point we find all 2nd order partial derivates and arrange them into a **Hessian Matrix**. 
$$\mathbf{H}(f) = 
\begin{bmatrix}
\frac{\partial^2 f}{\partial x_1^2} & \frac{\partial^2 f}{\partial x_1 \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_1 \partial x_n} \\
\frac{\partial^2 f}{\partial x_2 \partial x_1} & \frac{\partial^2 f}{\partial x_2^2} & \cdots & \frac{\partial^2 f}{\partial x_2 \partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial^2 f}{\partial x_n \partial x_1} & \frac{\partial^2 f}{\partial x_n \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_n^2}
\end{bmatrix}$$

$$
H_{ij} = \frac{\partial^2 f}{\partial x_i \partial x_j}, \quad i,j=1,\ldots,n.

$$
If det(H) > 0 and $f_{xx} < 0$ at the stationary point, then it is a local maximum.
If det(H) > 0 and $f_{xx} > 0$ at the stationary point, then it is a local minimum.
If det(H) < 0 at the stationary point, then it is a saddle point.
If det(H) = 0, then the test is inconclusive and higher order derivatives must be analysed.

---
# Approximations

To obtain a linear approximation at a point $x_0$

$$f(\mathbf{x}) \approx f(\mathbf{a}) + \nabla f(\mathbf{a}) \cdot (\mathbf{x} - \mathbf{a}) = f(\mathbf{a}) + \sum_{i=1}^n \frac{\partial f}{\partial x_i}(\mathbf{a})(x_i - a_i)$$

For a quadratic approximation:
$$f(\mathbf{x}) \approx f(\mathbf{a}) + \nabla f(\mathbf{a}) \cdot (\mathbf{x} - \mathbf{a}) + \frac{1}{2} (\mathbf{x} - \mathbf{a})^\top H_f(\mathbf{a}) (\mathbf{x} - \mathbf{a})$$
