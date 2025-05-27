# Translating and starting a program
- The compiler translates the high-level code into assembly language.
- The assembler turns the assembly code into machine language code (object file).
- The linker combines the object file with other machine language code (e.g. from already compiled and assembled libraries).
- The loader puts the executable into the memory.

## Assembler
The assembler makes two passes through the assembly code and turns it into the object file. On the first pass, the assembler assigns instruction addresses and finds all symbols, such as labels and global variable names, and makes a symbol table.![[Pasted image 20250516170708.png]]After the first pass of the assembler, instruction addresses have been assigned and the symbol table has been created. The second pass of the assembler generates the object file. The linker creates the executable by combining the object file with other machine language code, e.h. code corresponding to libraries. The loader puts the executable into the memory and its execution can start.
![[Pasted image 20250516171226.png]]
