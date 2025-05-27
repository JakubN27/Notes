
The relational data model is based on mathematical relations, and is the most widely used data model for structured data. Relations between data are stored in tables. For example, attribute values of a concrete instance of an entity are related because they belong to the same instance.

Schema of a relation R is represented using $R(A_1,A_2,...,A_n)$ for attributes $A_1,A_2,...,A_n$ 
Another example is Student(studentNo, firstName, surname). The ordering of attributes does not matter.

# Terminology
- **Relation**: table (with rows and columns). Only refers to the logical structure, not storage.
- **Attribute:** named column in a table (unique name)
- **Tuple:** A row in the table. Holds specific values for all attributes.
- **Domain:** (of an attribute), set of allowed values.
- **Cell**: value of a specific attribute in a tuple.
- **Degree:** number of attributes.
- **Cardinality**: number of tuples

## Keys
- **Key:** set of attributes whose values uniquely determine a tuple
- **Candidate key:** minimal set of attributes that is a key
- **Primary Key:** one candidate key selected to identify tuples.
- **Alternate key:** any candidate key that is not the primary key.
- **Simple key:** a key that consists of a single attribute
- **Composite key:** a key that consists of multiple attributes.
- **Foreign key:** A key that references the primary key of another table.