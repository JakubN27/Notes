Analysis of[[Sorting Algorithms#Iterative Sorting Algorithms| iterative algorithms]] is generally quite intuitive, as the number of iterations based on input size is implied in the algorithm, and you can essentially count the number of operations.
[[Sorting Algorithms#Recursive Sorting Algorithms|Recursive algorithms]] are generally a hybrid between iterative and strictly recursive (for example the partition function in quick sort is iterative). To analyse a recursive algorithm:
- look at recursive structure, for example with [[Sorting Algorithms#Merge Sort| merge sort]]:
	- split input of size n into two halves of equal size n/2 each
	- independently recurse into each half
	- merge the resulting sorted sequences
- This will normally give you a recurrence, pretty much trivially:
	![[Pasted image 20250419171730.png]]

Two methods for solving such recurrences:
1. Induction (guess, substitute, and verify)
2. Master Theorem 
## Solving recurrences by induction 
Assume a solution for T(n) and try to prove it holds true by induction