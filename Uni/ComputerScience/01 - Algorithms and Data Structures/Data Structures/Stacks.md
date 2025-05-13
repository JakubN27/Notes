A collection of objects that are inserted and removed according to the last-in-first-out (LIFO) principle.

A stack supports the following methods:  
 - push(e): Insert element e at the top of the stack.  
 - pop: Remove and return the top element of the stack; an error occurs if the stack is empty.
 
And possibly also:  
 - size: Return the number of elements in the stack.  
 - isEmpty: Return a Boolean indicating if the stack is empty.  
 - top: Return the top element in the stack, without removing it; an error occurs if the stack is empty.

## Implementation using arrays
A stack can be implemented in code using an [[Arrays and Lists#Array|Array]].
The array-based stack implementation is time efficient. The time taken by all methods does not depend on the size of the stack.
However the fixed size N of the array can be a serious limitation:
- If the size of the stack is much less than the size of the array, we waste memory
- If the size of the stack exceeds the size of the array, the implementation will generate an exception.
The array-based implementation of the stack has fixed capacity.
