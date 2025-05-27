# The C++ shell
An easy way to program in AVR assembly through the Arduino IDE, is to create a C++ shell file, and a separate linked file for the assembly code. In the setup() function, we will define the program's inputs and outputs. The loop() function repeats forever, which is usually the desirable behaviour in an embedded system.

# Directives
The assembly code contains some statements called directives. Directives do not correspond to assembly instructions, but the assembler will take them into account when compiling the assembly code into machine language. The use of directives, for example for defining a constant makes easier to develop and maintain assembly code. In AVR assembly a directive is presented by a dot (.).

The equ directive assigns a value to a label, and the label can then be used in later expressions. A label assigned a value by the equ directive is a constant, it cannot be redefined. We define a constant named delayVal with value 10000 by :
`.equ delayVal, 10000`
The directives `.global start` and `.global btnLED` declare the functions start and btnLED as global. This information will be used by the linker when it puts various pieces of code from several source files together.

# Declaring I/O pins
```
start:
	SBI DDRB, 4    ;set PB4 (delcare pin PB4 as output pin - LED)
	CBI DDRD, 2    ;clear PD2 (declare pin PD2 as input pin - e.g. a button)
	RET            ;return to setup()
```
First, we choose a pin for output (to light the LED light), and one pin for input(to recieve the signal for the light to start blinking). Here we chose pins PB4 and PD2, respectively.

# Reading I/O pins
```
btnLED:
	SBIC PIND, 2
	RJMP blink
	RJMP btnLED
```
The status of the input pin PF4 is recorded on register PIND. The SBIC instruction (skip if bit in I/O register is cleared) checks the corresponding bit in PIND and if it is 0 (cleared) skips one instruction. So if the bit has value 0 we skip one instruction and go to the jump with RJMP btnLED, so to the beginning of the function. Otherwise we jump with RJMP blink to the function that will blink the LED three times
