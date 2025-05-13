# Non-comparison based algorithms.
# Bucket Sort
Suppose the values in the list to be sorted can repeat but the values have a limit. Sorting, in this case, appears easier. It is possible to come up with an algorithm faster than O(n log(n)) which does not involve comparisons.

To sort n numbers, each taking a value in {0, . . . , k − 1} (the “range” of possible values is k):
Suppose the values are in the range 0..k-1; start with k empty buckets numbered 0 to k-1, scan the list and place element s[i] in bucket s[i], and then output the buckets in order
Do this for each digit in the number and they will be sorted without comparisons.
In pseudocode:
```
for j = 0 to k-1 do // initialize k buckets  
	b[j] = 0  
end for  
for i = 0 to n-1 do // place elements in their  
	b[S[i]] = b[S[i]] + 1 // appropriate buckets  
end for  
i = 0  
for j = 0 to k-1 do // place elements in buckets  
	for r = 1 to b[j] do // back in S  
		S[i] = j  
		i = i + 1  
	end for  
end for
```
If we were sorting values, each bucket is just a counter that we increment whenever a value matching the bucket's number is encountered. If we were sorting entries according to keys, then each bucket is a queue. Entries are enqueued into a matching bucket and dequeued back into the array after the scan.
The time complexity of a bucket sort is [[Theory|O(n + k)]] where k is the number of buckets. Since k is likely to be small compared to n, it is O(n) in the average case.

Bucket sort works as follows:

1. Set up an array of initially empty "buckets".
2. **Scatter**: Go over the original array, putting each object in its bucket.
3. Sort each non-empty bucket(using another algorithm like insertion sort).
4. **Gather**: Visit the buckets in order and put all elements back into the original array.

# Radix Sort
Radix sort is a non comparison sorting algorithm that sorts integers by grouping them by individual digits (or their radix). It works by repeatedly distributing elements into buckets based of their digits, from least significant to most significant. This process is often implemented using counting sort or bucket sort.
How it works:

1. **Distribution:** Elements are distributed into buckets based on the current digit being considered. 
2. **Collection:** Elements are collected from the buckets in order (0-9 for base 10). 
3. **Iteration:** This process is repeated for each digit position, starting with the least significant.

Drawback: If the range of items is large we need a large number of buckets, which increases time complexity.

