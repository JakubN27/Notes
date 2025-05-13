## Time Complexity

The time complexity of an algorithm can be expressed in terms of the number of basic operations used by the algorithm when the input has a particular size.
Examples of basic operations are:
- additions
- multiplications
- comparisons
- swaps
- assignments of values to variables

### Worst-case time complexity

The worst-case time complexity of an algorithm can be expressed in terms of the largest number of basic operations used by the algorithm when the input has a particular size. It tells us how many operations an algorithm requires to guarantee that it will produce a solution. IT is a standard way to estimate the efficiency of algorithms, and time complexity usually means worst-case complexity.

Since it is usually quite difficult to give an exact number of operations in the worst case, it is typically given as an upper bound, which gives us the possibility to estimate growth of the number of operations when input size increases. It is important to estimate the number of operations when the input size is large.

### Big-O notation
Let f and g be functions from the set of integers or the set of real  
numbers to the set of real numbers. We say that f is O(g) if there  
are constants C and k such that  
$$|f (x)| ≤ C · |g (x)|  $$
whenever $$x ≥ k.  $$
This is read as “f is big-O of g ”.

The definition says that after a certain point, namely after k, the  
absolute value of f (x) is bounded from above by C times the absolute value of g (x). The constants C and k in the definition of big-O notation are called witnesses to the relationship f (x) is O(g (x)).


Some orders that often occur in practice are:

| Big-O form                  | Name         |
|----------------------------|--------------|
| O(1)                       | constant     |
| O(log n)                   | logarithmic  |
| O(n)                       | linear       |
| O(n log n)                 | *n* log *n*  |
| O(n²)                      | quadratic    |
| O(n³)                      | cubic        |
| O(n^k) for k = 0, 1, 2, …  | polynomial   |
| O(c^n) for c > 1           | exponential  |
#### Sum and Product rules

The sum rule simply states that if a resultant time complexity is a sum of two different time complexities, the resultant Big-O notation is also the sum of two different Big-O notations.
The product rule states that when multiplying functions, the Big O complexity is the product of the individual Big O complexities.

### Big-Omega notation

The [[#Big-O notation]] is very useful to find reasonable upper bounds for growth rates, but does not really help much if we are interested in the best function that matches the growth rate. As a first step in this direction, we introduce a similar definition for lower bounds which is called big-omega notation

Definition: Let f (x) and g (x) be functions from the set of real numbers to the set of real numbers. We say that f (x) is Ω(g (x)) if there are positive constants C and k such that  
$$|f (x)| ≥ C · |g (x)|  $$
whenever $$x > k$$Note that this implies that f (x) is Ω(g (x)) if and only if g (x) is O(f (x)).

### Big-theta notation
Used for same order growth rates.
Let f (x) and g (x) be functions from the set of real numbers to the  
set of real numbers. We say that f (x) is Θ(g (x)) if f (x) is  
O(g (x)) and f (x) is Ω(g (x)).

### Little-o notation
Little-o provides a tool for disregarding or neglecting "small order" terms.
Definition: Let f (x) and g (x) be functions from the set of real numbers to the  
set of real numbers. We say that f (x) is o(g (x)) (“little-o” of  
g (x)) when  
$$
\lim_{x \to \infty} \frac{f(x)}{g(x)} = 0
$$
### Little-omega notation
ω is to o what Ω is to O
Definition: $$ω(g ) = {f : N → N | ∀C > 0 ∃k > 0 : f (n) > C · g (n) ∀n ≥ k}  $$
## Space Complexity

The space complexity of an algorithm is expressed in terms of the memory required by the algorithm for an input of a particular size. We will mainly be concerned with time complexity.




