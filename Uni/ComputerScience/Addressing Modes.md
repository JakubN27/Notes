# Register Only
- Uses registers for all source and destination operands.
- R-type instructions use Register Only addressing
# Immediate
- Uses registers and a 16-bit immediate as operands.
- Some of the I-type instructions use Immediate addressing (depending on how the 16-bit immediate is used)
# Base addressing
- Used in memory access instructions.
- Implemented by I-type instructions.
- The address of the memory operand is computed by adding the base address in register rs to a 16-bit offset stored in imm.
The instructions:
- lw: load word
- lb: load byte
- sb: store word
- sb: store byte
read and write data from and to the memory.
![[Pasted image 20250516164404.png]]
Notice the special assembly syntax for this I-type instruction. The word address 0 is the sum of the imm 0 and the value at register $0, which is always 0. [[MIPS#Registers]]
![[Pasted image 20250516164600.png]]


The assembly code `lw $t2, 32($0)` is translated to the machine language I-type instruction

| op     | rs    | rt    | imm                 |
| ------ | ----- | ----- | ------------------- |
| 35     | 0     | 10    | 32                  |
| 100011 | 00000 | 01010 | 0000 0000 0010 0000 |

The assembly code `sw $s21, 4($t1)` is translated to the machine language I-type instruction

| op     | rs    | rt    | imm                 |
| ------ | ----- | ----- | ------------------- |
| 43     | 9     | 17    | 4                   |
| 101011 | 01001 | 10001 | 0000 0000 0000 0100 |
# PC-Relative
Branching instructions can use the PC-relative addressing to specify the new values of the PC (Program Counter) if the branch is taken.

Consider the following MIPS Assembly code fragment:
```
0x40     loop: add $t1, $a0, $s0  
0x44           lb $t1, 0($t1)  
0x48           add $t2, $a1, $s0  
0x4C           sb $t1, 0($t2)  
0x50           addi $s0, $s0, 1  
0x54           bne $t1, $0, loop  
0x58           lw $s0, 0($sp)
```
On the left-hand side is the address of the word storing the instruction.
The branching instruction in this fragment is the I-type `bne` (branch if not equal)
It compared the values of registers $t1 and $0 and branches when they are not equal.
If the branch is taken, the new value of the PC is 0x40, corresponding to the label loop.
When we use assembly, we don't have to worry about how the new PC value will be computed, we just use labels.

When this is translated, to calculate the imm, we take the PC value immediately after the branching instruction, here 0x58, we subtract it from the branch target address (bta) here 0x40, and divide by 4. Here, result will be -6. Essentially, we calculate how many lines back the branching target is in the program (which is in the [[MIPS memory map#The text segment|text segment]]) 

# Pseudo-direct
In direct addressing, an address is specified in the instruction. MIPS does not support direct addressing, which would need 32-bit for the address and 6-bits for the opcode, while the instruction has 32-bits only. 
MIPS using pseudo-direct addressing in [[MIPS#J-type instructions|j-type instructions]] calculating the new value of the PX (the jump target address or JTA) ass follows:
- The two least significant bits are left to 0(instructions are word aligned and word addresses are taken in multiples of 4)
- The next 26 bits are taken from the addr field of the J-type instruction.
- The four most significant bits are again left to 0