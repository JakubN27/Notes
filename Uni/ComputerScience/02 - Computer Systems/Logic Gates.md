Logic gates take boolean inputs and output a single value.

# NOT gate
A note gate simply reverses a binary signal. It takes one input. If it gets a 0 it outputs 1 and vice versa.
To make a NOT gate out of [[Transistors]], connect a pMOS on top of an nMOS:
![[Pasted image 20250516134926.png|150]]
If A is high (1), then P1 is off and N1 is on and Y is connected to GND so Y is low (0).
If A is low (0), then P1 is on and N1 is off and Y is connected to $V_{DD}$ so Y is high (1).
# NAND gate
A NAND gate is the negation of AND. It takes two inputs and outputs one input. It will output 0 if both inputs are 1, otherwise it will output 0. It can be built from the following transistors:
![[Pasted image 20250516140417.png|250]]
