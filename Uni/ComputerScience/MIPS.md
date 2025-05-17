MIPS stands for Microprocessor without Interlocked Pipeline Stages.
It is used in embedded systems and consumer electronics.

A 32-bit RISC processor has 32-bit words, ~110 instructions in the instruction set and 32 general purpose registers:
# Registers
| Name      | Number | Use                     |
| --------- | ------ | ----------------------- |
| $0        | 0      | the constant value 0    |
| $at       | 1      | assembler temporary     |
| $v0 - $v1 | 2-3    | function return values  |
| $a0 - $a3 | 4-7    | function arguments      |
| $t0 - $t7 | 8-15   | temporary variables     |
| $s0 - $s7 | 16-23  | saved variables         |
| $t8 - $t9 | 24-25  | temporary variables     |
| $k0 - $k1 | 26-27  | OS temporaries          |
| $gp       | 28     | global pointer          |
| $sp       | 29     | stack pointer           |
| $fp       | 30     | frame pointer           |
| $ra       | 31     | function return address |

## MIPS Assembly
MIPS Assembly uses the same mnemonics as LMC, but the registers are used differently.
For example:
```
#High level code:
a = b + c

#MIPS assembly
add $s0, $s1, $s2
#$s0 = a, $s1 = b, $s2 = c


#High level code:
a = b + c - d

#MIPS assembly
sub $t0, $s2, $s3
add $s0, $s1, $t0

#$s3 = d, $t0 (temporary) = c - d
```

# Instruction Types
In LMC we had two types of instructions: 3 digit opcode, or a 1 digit opcode and 2 digit address (901 for example). Similarly in MIPS, there are three types of instructions:
- R-type
- I-type
- J-type
## R-type instruction format

| op     | rs    | rt    | rd    | shamt | funct  |
| ------ | ----- | ----- | ----- | ----- | ------ |
| 6 bits | 5 bit | 5 bit | 5 bit | 5 bit | 6 bits |
There are 3 register operands: 
- rs, rt are the source registers
- rd is the destination register. 
The other fields are:
- op: the opcode, it is always 0 for R-type instructions.
- funct: the function, essentially the second part of the opcode. If the first 6 bits of the instruction are 0, the computer understands it is an R-type. The function specifies which R-type instruction it is.
- shamt: the shift amount for shift instructions, otherwise it is 0.

### Example 1
The assembly code for adding the values in register 17 and 18 and putting the answer in register 16.
	add $s0, $s1, $s2 
is translated to machine language as follows:

| op     | rs    | rt    | rd    | shamt  | funct   |
| ------ | ----- | ----- | ----- | ------ | ------- |
| 000000 | 10001 | 10010 | 10000 | 000000 | 1000000 |
| 0      | 17    | 18    | 16    | 0      | 32      |

### Example 2
Subtracting register 13 from register 11 and putting the answer in register 8:

| op     | rs    | rt    | rd    | shamt  | funct   |
| ------ | ----- | ----- | ----- | ------ | ------- |
| 000000 | 01011 | 01101 | 01000 | 000000 | 1000010 |
| 0      | 11    | 13    | 8     | 0      | 34      |
## I-type instructions
| op     | rs     | rt     | imm     |
| ------ | ------ | ------ | ------- |
| 6 bits | 5 bits | 5 bits | 16 bits |
Three operands:
- rs, rt: register operands
- imm: 16-bit immediate written in two's complement
- rs and imm are used as source operands. rt is used as a source in some instructions and a destination in some others.
The other field:
- op: the opcode. The instruction is completely determined by the opcode.
### Example 1
Adding the number 5 to register 17 and putting the answer in register 16.
addi $s0, $s1, 5

| op     | rs    | rt    | imm                 |
| ------ | ----- | ----- | ------------------- |
| 8      | 17    | 16    | 5                   |
| 001000 | 10001 | 10000 | 0000 0000 0000 0101 |
### Example 2
Loading the number 5 to the register 16
li $s0, 5

| op     | rs    | rt    | imm                 |
| ------ | ----- | ----- | ------------------- |
| 13     | 0     | 16    | 5                   |
| 001101 | 00000 | 10000 | 0000 0000 0000 0101 |
Implemented by the logical OR I-type instruction:
ori $s0, $s0, 5

## J-type instructions
| op     | addr    |
| ------ | ------- |
| 6 bits | 26 bits |
addr: 26-bit address operand
op: the opcode, the instruction is completely determined by the opcode
Used for jump instructions such as j. The compiler will create a 32-bit address fro the 26 bits of addr.