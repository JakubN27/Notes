## Recursion

A recursive algorithm is an algorithm that calls itself to do part of its work. A recursive algorithm must have a base case. It must change its state and move towards the base case.

### Memorisation

Storing the result of a computation so that it can be subsequently retrieved without repeating the computation is called memorisation. [[Hash Tables]] are a good choice of data structure to implement memorisation. It can greatly improve the performance of recursive algorithms.

## Backtracking
Backtracking is a technique for problems with many candidate solutions but too many to try. The general idea is to build up the solution one step at a time and go back or backtrack when it is unable to continue further.