# Microcontroller
Microcontrollers are integrated devices (computers in a chip) consisting of:
- a microprocessor (including ALU, PC, and registers)
- memory (Flash, SRAM)
- input/output
They are used in embedded systems, that is, special purpose computer systems designed to perform dedicated functions, often in real-time.
The program is usually stored in Flash memory and it might never change during the lifetime of the microcontroller.

# Main characteristics
Arduino UNO uses the ATmega328P microcontroller:
- Harvard architecture
- 8-bit processor (8-bit registers, 8-bit bus)
- 16-bit words (but some instructions are 32-bit)

# Registers
32 general purpose 8-bit registers. They are also mapped on the SRAM memory. Other SRAM memory locations are also used as 'registers', that is, they are designated as registers.
The six 8-bit registers R26-R31 should be treated as three 16-bit registers, named X Y and Z. They are used for indirect addressing.

## Status Register
The status register is an 8-bit register, not one of the 32 general purpose registers we have already discussed. Its 8 bits are used as flags, and in the documentation of AVR assembly have standard names.
In one of the usages of the status register, arithmetic and logical instructions may update some of the status register bits, depending on the result of the operation. This information can then be used by the next instruction.

# Memory map
The two main memory spaces (Harvard architecture, separates data and instructions), the data memory (SRAM and EEPROM) and the Program Memory (Flash). The same architecture comes in various memory sizes (and perhaps some additional capabilities)

### Program Memory
Since AVR instructions are 16 or 32 bits wide, the flash if organised as 2/4/8 16k x 16. (16k x 16 in 328P). It is divided into two sections: the boot loader section and application program section. Arduino's flash has an endurance of at least 10000 write/erase cycles. The program counter is 14 bits wide, this addressing the 16k program memory locations.

### Data memory (SRAM)
The static random access memory (SRAM) is divided into sections used as: 
- mapping space of ALU registers
- I/O registers and extended I/O registers
- internal SRAM

### EEPROM memory
1KB of EEPROM (electrically erasable programmable read only memory). It is organised as a separate space for storing data. Arduino's EEPROM has an endurance of at least 100000 write/erase cycles.

# I/O
ATmega328P's I/O pins are grouped into 3 ports:
- B (digital)
- C (analog)
- D (digital)

## Data direction registers
The direction of each pin of a port (input or ouput) is controlled by 8-bit data direction registers:
- DDRB (data direction register B)
- DDRC (data direction register C)
- DDRD (data direction register D)
We do not have to use the ecplicit memory locations of these registers. The assembler recognises the names DDRB, DDRC and DDRD. 

### Example: setting pin direction
Whether a pin is used as input or output is controlled by a single bit. When a bit is 1 (also known as being set), the corresponding pin is output. When it is 0 (also known as being cleared), then the corresponding pin in input.
We can control a pin's direction by manipulating single values of a register with the instructions SBI(set bit) and CBI(clear bit)
```
	SBI DDRB, 4.    ;set PB4.  (declare pin PB4 as output)
	CBI DDRD, 2.    ;clear PD2 (declare pin PD2 as input)
```
Assume that a pin has been declared as an input pin. At any specific point in time, this pin has a certain status. Either there is an incoming electric signal or not. This information is recorded on the corresponding bit of the corresponding I/O register, PINB, PINC, and PIND. 
Example: In the previous example, we declared PD2 as input. The second bit (PIND2) of the register PIND records the current status of that pin. Its value could change continuously.

Assume that a pin has been declared as output pin. At any specific moment in the time, w cam set this pin to a certain status. Either we send an out-coming electric signal through that pin, or not. This is controlled by the corresponding bit of the I/O registers PORTB, PORTC, and PORTD.
Example:L in the previous example we declared PB4 as input. The second bit (PORTB ,4) of the register PORTB controls the current status of that pin. By setting that bit, we send electric current through that pin. By clearing it, the electric current stops.