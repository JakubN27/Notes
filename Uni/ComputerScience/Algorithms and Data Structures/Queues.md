A queue is a collection of objects that are inserted and removed according to the firsT-in-first-out (FIFO) principle. Element access and deletion are restricted to the first element in the sequence which is called the front of the queue And insertion is retricted to the end (rear).

A queue supports the following methods:
- enqueue(e): Insert element e at the rear of the queue
- dequeue: Remove and return from the queue the lement at the front; an error occurs if the queue is empty.
And possibly also:
- size: Return the number of elements in the queue.
- isEmpty: Return a Boolean indicating if the queue is empty
- front: Return the front element of the queue, without removing it; an error occurs if the queue is empty.
