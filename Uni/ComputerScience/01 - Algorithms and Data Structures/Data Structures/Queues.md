A queue is a collection of objects that are inserted and removed according to the first-in-first-out (FIFO) principle. Element access and deletion are restricted to the first element in the sequence which is called the front of the queue And insertion is restricted to the end (rear).

A queue supports the following methods:
- enqueue(e): Insert element e at the rear of the queue
- dequeue: Remove and return from the queue the element at the front; an error occurs if the queue is empty.
And possibly also:
- size: Return the number of elements in the queue.
- isEmpty: Return a Boolean indicating if the queue is empty
- front: Return the front element of the queue, without removing it; an error occurs if the queue is empty.

# Priority Queue
A priority queue is a specialised queue-like data structure where each element has an associated priority. It operates on the principle that items with higher priorities are served before those with lower priorities. This makes it useful in scenarios where some tasks need to be processed faster than others, regardless of their order of arrival.

Priority queues are often implemented using [[Heaps]] which efficiently manage the priority based ordering. They can also be implemented using [[Binary Search Trees]] or [[Arrays and Lists#Linked list|linked lists]].