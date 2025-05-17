Combinatorial / combinational circuits (Output depends only on current input):
- Adders - add the content of two registers
- Decoders - decodes an n-digit binary number into 2^n data lines
- Multiplexors - uses a binary number to select an input.
Sequential circuits (Output depends on state and input, i.e. history of input):
- Latches/flip-flops - basic memory element.

# Adders
## Half-adder
A half adder adds 2 bits, and returns a sum and a carry.
![[Pasted image 20250516144237.png]]

## Full-adders
A full adder combines half adders, and now takes 3 inputs instead of two as it takes in a previous carry value.
![[Pasted image 20250516144332.png]]
These can be chained to add any two binary numbers, wit ha full adder for each bit.
![[Pasted image 20250516144511.png]]

# Decoder
A decoder has N inputs and $2^N$ outputs. Asserts exactly one of its inputs depending on teh binary number represented by the N inputs. 
![[Pasted image 20250516144704.png]]
2 bit decoder:
![[Pasted image 20250516144718.png]]
The truth table essentially returns the n-th permutation of a binary number, and the 1s are on a diagonal. 
![[Pasted image 20250516144808.png]]

# Multiplexor 
A multiplexor chooses 1 of many inputs to steer to its single output under the direction of control inputs. if the input to a circuit can come from several places, a mux is one way to funnel the multiples sources selectively to a single input.
![[Pasted image 20250516144931.png]]
The following table can be remembered by just counting in binary, and the first bit decides which one of the next two is picked. 
![[Pasted image 20250516144945.png]]
A multiplexor has $k+2^k$ inputs and 1 output. The first k inputs( the selector S) represent a binary number. The output takes the value of one of the remaining $2^k$ inputs, the one indexed by the selector.
![[Pasted image 20250516151205.png]]

# Tristate buffer
In contrast to a normal buffer which is either 1 or 0 at its output, a tristate buffer can be electrically disconnected from the bus wire, so if will have no effect on any other signals currently on the bus.
![[Pasted image 20250516151042.png]]
![[Pasted image 20250516151124.png]]