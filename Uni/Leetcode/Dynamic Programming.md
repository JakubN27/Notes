# Naive Recursive
- Doesn't use DP, big runtime, very slow.
- However it is useful since its easy to optimise using top-down DP memoisation
- For example for the fibonacci number problem, we define the naive recursive solution as F(n) = F(n-1) + F(n-2)
- In code this is:
- ``
  ```
  def fib(n):
		  if n== 0:
			  return 0 
		  if n == 1:
			  return 1
		  
		  return fib(n-2) + fib(n-1)
  ```
# Top-Down DP Memoization
- The naive solution is inherently recursive, where the function calls itself until a base case is reached. 
- ![[Pasted image 20251005210005.png]]
- In this function call tree many of the calls are repeated many times, leading to a very inefficient solution. Using Top down memoization we can 'remember' the results and not have to compute them repeatedly.
- Generally a we use a dictionary, starting with our base cases {0: 0, 1:1} and this is essentially caching or sometimes known as 'memo'.
- This saves us from going down branches that have been previously calculated.
- To implement this in code we define a helper function
```
def fib(n):
	memo = {
		0:0,
		1:1
		}
	
	def f(x):
		if x in memo:
			return memo[x]
		else:
			memo[x] = f(x-1) + f(x-2)
			return memo[x]
			
	return f(n)
```
This approach gives time and space complexity of O(n)
# Bottom-Up DP/Tabulation
- The bottom up approach avoids recursion
- We essentially just build up an array until we find the result we need, hence the 'bottom up' approach.
- We define a list with base cases and calculate further entries. In this case we start with an array of size n. 
- In code: 
```
def fib(n):
	if n == 0:
		return 0
	if n == 1:
		return 1
	
	dp = [0] * (n+1)
	dp[0] = 0
	dp[1] = 1
	
	for i in range(2, n+1):
		dp[i] = dp[i-2] + dp[i-1]
	
	return dp[n]
```
Note the "next element in array" is very similar to the naive recursive approach.
# Constant Space Solution
There is an optimization for the bottom up approach, where you only look at the elements in the array which are needed, since for Fibonacci in this instance we only need the 2 previous elements.
```
def fib(n):
	if n == 0:
		return 0
	if n == 1:
		return 1
	
	prev = 0
	curr = 1
	
	for i in range(2, n+1):
		prev, cur = cur, prev+cur
	
	return cur
```

# Example
## Longest Common Sub sequence

- For sub sequence problems we typically need a two dimensional DP solution.
- We need to construct a matrix of common characters in the two strings as such:
- ![[Pasted image 20251005215340.png]]
- When we match a pair of common characters we can 'eliminate' its row and column and work on the remaining subproblem.
- However if we match different characters for example b and c, we cannot just continue diagonally so we end up with 2 subproblems, by continuing either down or to the right.
When we will the table completely we will have our longest common substring as the max value
