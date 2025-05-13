# Iterative Sorting Algorithms
## Insertion Sort
In pseudocode:
```
for j = 2 to n do  
	x = aj  
	i = j − 1  
	while i > 0 and ai > x do  
		ai+1 = ai  
		i = i − 1  
	end while  
	ai+1 = x  
end for
```
- When j has a certain value, it inserts the j<sup>th</sup> element into already sorted sequence a<sub>1</sub> ... a<sub>j-1</sub> yielding sorted a<sub>1</sub> ... a<sub>j</sub> 
- Can be proved correct by using invariant “after j-th iteration first j+1 elements are in order”
- running time between n-1 and n(n-1)/2 meaning worst case O(n^2)

## Selection Sort
In pseudocode: 
``` 
for i = 1 to n − 1 do  
	elem = ai  
	pos = i  
	for j = i + 1 to n do  
		if aj < elem then  
			elem = aj  
			pos = j  
		end if  
	end for  
	swap ai and apos  
end for
```
- Invariant: after i-th iteration position 1, .., i contain the overall i many smallest elements in order
- Not necessarily the first i elements (as it was in InsertionSort)
- In i-th iteration of outer loop, we search the i-th smallest element element in remainder (positions i + 1, ..., n) of input and swap it into position i 
	- elem keeps track of current idea of value i-th smallest element
	- pos keeps track of current idea of position of i-th smallest element
- Time complexity: O(n^2)

## Bubble Sort
In psuedocode:
```
for i = n downto 2 do  
	for j = 2 to i do  
		if aj−1 > aj then  
			swap aj−1 and aj  
		end if  
	end for  
end for
```
- Invariant: after the iteration for i of the outer for-loop, positions i, ..., n contain the overall n - i + 1 many largest elements in order
- Time complexity: O(n^2)
- Variation: Terminate of no swap executed during inner for-loop.

# Recursive Sorting Algorithms
Recursive sorting algorithms work based on a "divide and conquer" basis, and repeat themselves on smaller subsets of the original data, by calling themselves within the algorithm.

## Merge Sort
In pseudocode:
```
if length(m) ≤ 1 then  
	return m  
end if  
int middle = length(m) / 2  
list left, right, leftsorted, rightsorted  
left = m[1..middle]  
right = m[middle+1..length(m)]  
leftsorted = MergeSort(left)  
rightsorted = MergeSort(right)  
return Merge(leftsorted, rightsorted)
```

Essentially, keep halving the list until they're units, and merge together in the correct order. But how do you actually merge two sorted sequences?
Suppose two sorted sequences given as arguments, say *left* and *right*.
Start with initially empty result sequence.
If both left and right aren't empty then look at leftmost element of each, say *l1* and *r1.* If *l1 < r1* then append *l1* to the result, otherwise append *r1*. If either list is empty, append the remaining elements of the other list. Repeat until both empty.
```
list result  
	if length(left) > 0 and length(right) > 0 then  
		if first(left) ≤ first(right) then  
			append first(left) to result  
			left = rest(left)  
		else  
			append first(right) to result  
			right = rest(right)  
		end if  
		append left to result  
		left = empty list  
	else                               // length(right) > 0  
		append right to result  
		right = empty list  
	end if  
end while  
return result
```
- Merge sort is the simplest recursive sorting algorithm
- Its worst cases are a lot better than worst cases of iterative algorithms.
- But its good cases may be worse.
- Merge Sort generally requires around *nlog(n)* steps to sort any n numbers.
- Insertion sort can get away with *n*  in its best case, but n^2 in its worst.

## Quick Sort
Another divide and conquer algorithm:
- Split input into two parts.
- Recursively sort them one after the other.
- Concatenate the resulting sorted sequences.
We say concatenate rather than merge, since quick sort differs from merge sort in the fact that it is guaranteed the subproblems will already be in order. i.e. all elements in the left sublist will be smaller than any element in the right sublist.\
- Quick sort picks an element to use as a 'pivot' and partitions the rest of the list based on whether the elements are bigger or smaller than the pivot, smaller going to the left and bigger to the right.
- Parts can vastly vary in size, differently to merge sort's equal partitions.
- Quick sort does the difficult bit prior to recursing which allows us to simply concatenate afterwards.
A basic pseudocode implementation of quicksort:
```
if (left < right) then   
	pivot = Partition (A, left, right)  
	QuickSort (A, left, pivot-1)  
	QuickSort (A, pivot+1, right)  
end if
```
The pivot element depends on the partition() function which can vary.

### The partitioning function 
The partitioning function determined how the pivot element is selected. It does not sort, but simply moves the elements smaller than the pivot to the left of the pivot in the order they are found.
An example partition function which simply choose the right most element as the pivot:
```
int x = A[right]  
int i = left-1  
for j=left to right-1 do  
	if A[j] < x then  
		i = i+1  
		swap A[i] and A[j]  
	end if  
end for  
swap A[i+1] and A[right]  
return i+1 // pivot position after partitioning
```
An example of an optimised pivot selection algorithm is the [[Median of Medians]] algorithm.