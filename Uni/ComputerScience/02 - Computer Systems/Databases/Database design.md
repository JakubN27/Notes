# Three level ANSI-SPARC Architecture
This is a three level model that defines how data is represented and managed in a database system. It includes the external, conceptual, and internal levels of data abstraction.
We maintain data independence on each level, as each is just an abstract representation of the lower levels.
## External Level
This level defines how different users and applications view and interact with data. It consists of multiple schemas tailored to specific user needs and preferences, ensuring data is customised without affecting the underlying data structure.

## Conceptual Level
This level defines the logical structure and meaning of data, independent of any physical implementation or user view. It provides a comprehensive data model that captures the business logic and semantics of data.

## Internal Level
This level defines the physical storage and organisation of data, taking into account the characteristics and limitations of the hardware and software systems.

# Conceptual Design
A conceptual design starts as a high level model which uses [[entity-relationship modelling]]. This identifies appropriate entities, attributes, relationships and constraints, based on the users requirements and independent of any physical constrained. It serves as the fundamental understanding of the system.

# Logical Design
We construct the [[Relational Data Model]]l using the conceptual design by mapping entities and relationships to tables. We use [[Dependencies]] techniques to eliminate data redundancies and anomalies.



