- word: 32-bits (in MIPS, high level architectural choice)
- byte: 8-bits(always, by definition)
MIPS uses 32-bit memory addresses and memory is byte addressable.
![[Pasted image 20250516160430.png]]

With 32- bit addresses, the MIPS address space spans 2^32 bytes = 4 gigabytes (GB)
Word addresses are divisible by 4 (i.e. the two least significant bits are 0) and range from 0 to 0xFFFFFFFC. The MIPS architecture divides the address space into four parts:
- [[#The text segment]]
- [[#The global data segment]]
- [[#The dynamic data segment]]
- [[#Reserved segments]]

## The text segment
The text segment stores the machine language program. It can store almost 256 MB of code. The four most significant bits of any word address in text segment are all 0 (and the two least significant)

Thus, the 26 bits of the addr field in a [[MIPS#J-type instructions|j-type instruction]] suffice to specify the address of any instruction stored in the text segment.
## The global data segment
The global data segment stores global variables, which can be seen by all functions in a program. It can store 64KB of data. Global variables are accessed using the pointer $gp.
By convention, we initialise $gp at the middle of the global data segment at value 0x10008000
The value of $gp stays constant throughout execution, and global variables are addressed as offsets from 0x10008000.
## The dynamic data segment
The dynamic data segment stores data that are dynamically allocated and deallocated throughout the execution of the program. It is the largest segment of memory used by a program, spanning almost 2GB of the address space.
Data in this segment are stored in a [[Stacks|stack]] and a [[Heaps|heap]]. 

## Reserved segments
The reserved segments are used by the operating system and cannot directly be used by the program.

