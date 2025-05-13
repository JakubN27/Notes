Heaps are a type of [[Trees|tree]], but typically assumed to be stored in a flat [[Arrays and Lists|array]]. So physically, they are a linear array, but logically they are a binary tree, filled on all levels except lowest.

Each tree node corresponds to an element in the array. The tree is complete on all levels except lowest, and is filled left to right. It differs from [[Binary Search Trees]] since the elements are ordered differently.

# Max Heaps
For every node excluding the root, the value is at most that of its parent. 
$$A[parent[i]] \geq A[i]$$
The largest element is stored at the root, and in any subtree no values are larger than the value stored at the subtree root.

# Min Heaps
For every node excluding the root, the value is at least that of its parent. 
$$A[parent[i]] \leq A[i]$$
The smallest element is stored at the root, and in any subtree no values are smaller than the value stored at the subtree root.

# Properties
It is a binary tree with the following properties:
- It is a complete binary tree
- The value stored at a node is greater or equal to the values stored at the children (for max heaps)
- 
Array indices associated with relative position in the tree are as follows:
- The root is in $A[i]$
- $left[i] = A[2^i]$
- $right[i] = A[2^i + 1]$
- $parent[i] = A[i/2]$ - integer division, rounds down.
So, v.left.index = 2*(v.index) and so on. This works because each level have twice the number of elements.
# Insertion
To insert an element into a binary max heap H:
1) Add the new element node to bottom left H.
2) If the new node value is bigger than its parent, swap their values. Set the parent node as new node and repeat step 2
3) Otherwise, exit.
Step 2 is called **heapify**.

# Use-cases
Heaps are a very good data structure for [[Queues#Priority Queue|priority queues]], and for sorting. Given a sequence of objects with different priorities, we want to deal with highest priority items first. So as to support priority queues we need to extract maximum element from collection, quickly: 
```
HeapExtractMax(A):
	ret = A[1]    // biggest element (highest priority)
	A[1] = A[HeapSize(A)]
	HeapSize(A) -= 1
	Heapify(A, 1, HeapSize(A))
	return ret
```
This essentially returns the top element of the heap, and replaces it with the last one (bottom level on the right). Then it heapifies to maintain its order

# Heapify
```
Heapify(A, v, n)
	// n is heap size
	// find largest among v and 2v (left child)
	largest = v
	if 2v <= n and A[2v] > A[largest]
		// find largest among winner above and 2v + 1 (right child)
		if 2v + 1 <= n and A[2v + 1] > A[largest] 
			largest = 2v + 1
		if largest != v then
			swap A[v], A[largest]
			Heapify(A, largest, n)
```
Heapify runs in linear time based on the height of the tree, which is also O(log n).
In simpler words: A node is checked against its left node to find largest, and the larges is checked against the right child. The largest of the three is swapped with the original node. It recursively follows the tree down, through the side that just got swapped.

# BuildHeap
Task: given array A with n arbitrary numbers stored in it, convert A into a heap. The arbitrary tree structure is populated with no regard for size of elements, then ordered with heapify.
```
BuildHeap(A, n):
	for i=n down to 1:
		Heapify(A, i, n)
```
This heapifies the nodes in order, bottom to top, starting from the leaves. Leaves cant be heapified, so remain as they are.
Running time - a loose upper bounds is O(log n) x O(n) = O(n log n)
It is possible to build a heap from an unordered array in linear time, O(n)

# Extraction
To extract/ delete a node from a heap, we replace it with the last node, then heapify from the top. Data is always deleted from the root of a heap.

# HeapSort
A sorting algorithm based on heaps. It can be implemented on an unordered array by calling BuildHeap on the array, then repeatedly calling HeapExtractMin until empty
```
HeapSort(A, Length(A))
	for i = Length(A) downto 2 do
		swap A[i] and A[1]
		HeapSize(A) = HeapSize(A) -1
		Heapify(A, 1, HeapSize(A))
	endfor
```
Running time: O(n log n)