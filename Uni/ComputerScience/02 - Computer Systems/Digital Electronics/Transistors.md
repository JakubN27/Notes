[[Logic Gates]] are what drive the logic behind computers, and they are built up of transistors. There are two types of transistors, nMOS and pMOS. Transistors work by connecting ports in a circuit based on the voltage of a third one. 

# nMOS transistors
![[Pasted image 20250516133847.png]]

Ports d and s are connected or disconnected depending on the voltage of g. It will allow the signal through when g is off, and it will not when g in on. 

# pMOS transistors

![[Pasted image 20250516133913.png]]Ports d and s are connected or disconnected depending on the voltage of g. It will allow the signal through when g is on, and it will not when g in off. 

# Voltage
In reality, a chip does not deal in 0s and 1s. The voltages are real numbers between 0 and 5V typically. We can take 0V to be false or 0 and 5V to be true or 1, but we need to tolerate noise, as voltages aren't perfect and will fluctuate, which is why we need to use logic levels. 
![[Pasted image 20250516134435.png]]

# Moore's Law
Moores law states that transistor density doubles every 2 year or that the speed of computer processors doubles every 18 months.