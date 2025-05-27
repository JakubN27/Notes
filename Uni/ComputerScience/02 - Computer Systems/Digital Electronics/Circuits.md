
A circuit is a network that processes discrete-valued variables.
A circuit has:
- one or more discrete valued input terminals
- one or more discrete values output terminals
- a specification of the relationship between inputs and ouputs
- a specification of the delay between inputs changing and outputs responding (like a processing time.
A circuit is made up of elements and nodes:
- An element is itself a circuit with inputs outputs and specs.
- a node is a wire joining elements, whose voltage conveys a discrete valued variable.

# Combinational Logic
We wish to design very large circuits to perform functions for us. We will restrict what we allow, for now, firstly to combinational logic and circuits. Combinational logic rules:
- Individual [[Logic Gates|gates]] are combinational circuits.
- Every circuit element must be a combinational circuit.
- Every node is either an input to the circuit connecting to exactly one output of a circuit element
- The circuit has no cyclic paths - every path through the circuit visits any node at most once.
