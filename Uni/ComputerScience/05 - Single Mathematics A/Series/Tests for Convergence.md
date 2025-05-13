# Comparison Test

- If the infinite series $\sum b_n$**converges** and $0 \leq a_n \leq b_n$ for all sufficiently large $n$ (that is, for all $n > N$ for some fixed value $N$), then the infinite series $\sum a_n$ also **converges**.
- If the infinite series $\sum b_n$ **diverges** and $0 \leq b_n \leq a_n$ for all sufficiently large $n$, then the infinite series $\sum a_n$ also **diverges**.
- The series having larger terms is sometimes said to **dominate** (or **eventually dominate**) the series with smaller terms.

# Limit Comparison Test

- Suppose that two series $\sum{a_n}$ and $\sum{b_n}$ with $a_n\geq 0, b_n>0$ for all $n$. Then if $$\lim_{n\to\infty}{\frac{a_n}{b_n}} = c$$ with $0<c<\infty$, then either both series converge or both series diverge.  

# Ratio Test

For an infinite series, $\sum_{n=1}^{\infty}a_n$ the ratio test is used to determine absolute convergence.
The test makes use of the limit 
$$L = \lim_{n\to\infty}\left|\frac{a_{n+1}}{a_n}\right|$$
- if L < 1 then the series converges absolutely
- if L > 1 then the series diverges
- if L = 1 or the limit fails to exist, then the test is inconclusive, because there exist both convergent and divergent series that satisfy this case

# Alternating sign test
The alternating sign test states the following: An alternating series $\sum a_n$ converges if $|a_n| \to 0$ as $n \to \infty$ 
and 
$|a_{n+1}| < |a_n|$ for an n > N for some N (above a certain value N).
This means that $\sum a_n$ will at least converge conditionally, not necessarily absolutely

In simpler words, if each term gets smaller, and they tend to 0, an alternating series will converge conditionally, and possibly absolutely.