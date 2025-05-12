The Taylor series can approximate any function as a polynomial at a point a. The formula for the taylor series is:
$$\sum_{n=0}^{\infty} \frac{(x-a)^n f^n(a)}{n!}$$

The polynomial becomes increasingly accurate to the original formula as n increases.

# Lagrange form of the remainder
The Lagrange remainder provides an estimate for the error in approximating a function using its Taylor polynomial. It expresses the remainder as a function of the (n+1)-th derivative evaluated at some point c between a and x.


## Taylor's theorem
Taylor's theorem states that if f(x) is differentiable N+1 times in a neighbourhood of a, x id a point in this neighbour hood and $f^{N+1}$ is continuous between a and x, then $f (x) = p_{N,a}(x) + R_{N +1,a}(x)$ 
where $p_{N,a}(x)$ is the Nth Taylor polynomial for f(x) around a, and $R_{N +1,a}(x)$ is the Nth remainder term
$$R_{N +1,a}(x) = \frac{f^{(N+1)} (\xi)}{(N+1)!} (x-a)^{N+1} $$ for some value $\xi$ in the interval between a and x. This is known as the Lagrange form of the remainder.