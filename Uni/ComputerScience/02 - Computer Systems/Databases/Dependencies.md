
## Functional dependencies
If A and B are two sets of attributes in a relation, we say "B is functionally dependent on A" or "A determines B". A and B are sets, meaning they can consist of multiple attributes. Informally, A-> B means that if you know the values of A, you can derive the values of b. For example id -> college and college -> collegeAddress.

### Full Functional Dependency
B is functionally dependent on A and B is not functionally dependent on any proper subset of A. Any dependency on a single attribute is full

### Partial Functional Dependency
B is functionally dependent on A and B remains functionally dependent on at least one proper subset of A.

### Transitive Functional Dependency
If A-> B and B->C then C is transitively dependent on A via B

# Closure of a set of dependencies
We can determine all functional dependencies given a set of functional dependencies F by finding its closure $F^+$. We need a set of inference rules to compute $F^+$. These are Armstrong's axioms:
- **Reflexivity**: If B is a subset of A, then A -> B
- **Augmentation:** If A -> B, then A,C -> B,C
- **Transitivity:** If A -> B and B -> C then A -> C
Further rules which can be derived from the axioms:
- **Decomposition:**: if A -> B, C, then A -> B and A -> C
- **Union:** If A -> B and A -> C then A -> B, C
The closure $F^+$ of F can be computed by starting with all dependencies in F, repeatedly applying Armstrong's axioms and adding any new dependencies discovered in this way.