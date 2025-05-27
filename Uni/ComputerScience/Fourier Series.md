Recall the [[Taylor Series]], which requires f(x) to be infinitely differentiable. This makes it useful for discontinuous functions.

We will propose a new series expansion that uses trigonometric functions. It is a function as an infinite sum of sines and cosines such that the series converges to the function value at (almost) any point. Wherever it does not converge exactly, it converges to a sensible value.

For a function $f(x), -\pi < x < \pi$, we will construct a series for $f$ of the form:
$$f(x) \approx \frac{a_0}{2} + \sum^{\infty}_{n=1}{a_ncos(nx) + b_nsin(nx)}$$
Where the cos and sin terms reach higher and higher frequency as n grows, converging to a continuous function as n tends to infinity. 

The range $-\pi < x < \pi$ is no real restriction - we can always scale a n arbitrary function f on a range (a,b) by setting:
$$f(x) = g\Bigg(\bigg(x-\frac{b+a}{2}\bigg)\frac{2\pi}{b-a}\Bigg)$$
where g(x) is a function on $-\pi < x < \pi$

## Fourier Coefficients
To find the coefficients $a_n, b_n$ we calculate:
$$a_n = \frac{1}{\pi}\int^\pi_{-\pi}f(x)cos(nx)$$
$$b_n = \frac{1}{\pi} \int^\pi_{-\pi}f(x)sin(nx)$$
