Databases can be normalised from 1st-3rd form to be made more efficient.
# Anomalies
- **Insertion anomaly:** new records need to duplicate existing data
- **Modification anomaly:** modifying only one value may lead to inconsistencies
- **Deletion anomaly** losing other data as a result of deleting one
# First Normal Form (1NF)
A table is in 1NF if it has:
- no repeating groups/multi-value attributes (every cell has one value)
If there is a fixed number of repetitions, you may use separate attributes.

# Second Normal Form (2NF)
A table is in 2NF if:
 - It is in 1NF
 - It has no [[Dependencies#Partial Functional Dependency|partial functional dependencies]] - every non-key attribute is dependent on the whole primary key.
 2NF is only relevant for relations with composite keys. To normalise into 2NF we remove the partially dependent attributes and place them in a new relation along with a copy of their determinant.
# Third Normal Form (3NF)
A table is in 3NF if:
- It is in 3NF
- It has no [[Dependencies#Transitive Functional Dependency|transitive functional dependencies]].
Recall [[Dependencies#Closure of a set of dependencies|Armstrong's axiom]] on transitivity. To resolve, we remove the transitively dependent attributes and place them in a new relation along with a copy of their determinant.