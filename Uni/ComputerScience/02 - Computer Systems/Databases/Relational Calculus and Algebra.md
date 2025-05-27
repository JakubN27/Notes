There are two types of DB languages: declarative and procedural. SQL is declarative, and its declarative queries are internally transformed to procedural form. 
Relations are considered as sets of elements where an element is a tuple of attribute values and each row in a table specifies one element of the set.

Relational calculus and algebra are equivalent languages. They can be used to define and create the same sets. For every calculus expression there is one or more algebraic expressions. They are not user friendly, but are used as a formal basis to define and compare querying languages. Modern query languages like SQL are relationally complete (can produce any relation that relational algebra/calculus can), have additional operations (they have more expressive power than relational calculus/algebra) but are still not Turing complete.

# Relational Calculus
Relational Calculus is declarative. It uses theoretic expressions (predicate calculus/first-order logic). It defines a new set based on one more more existing ones.

A predicate is a function that returns true/false given certain arguments. A proposition is the expression obtained when replacing values for the arguments of a predicate (i.e. a proposition is either true or false). Let $P(x)$ and $Q(x)$ be two predicates with an argument x. Then:
- The set of all x such that both $P(x)$ and $Q(x)$ are true is $${x|P(x)\land Q(x)}$$
- The set of all x such that $P(x)$ or $Q(x)$ are true is $${x|P(x)\lor Q(x)}$$
- The set of all x such that $P(x)$ is not true is $${x|\textasciitilde P(x)}$$
- 
# Relational Algebra 
Relational Algebra uses operators to construct a new set from one or more existing ones.
