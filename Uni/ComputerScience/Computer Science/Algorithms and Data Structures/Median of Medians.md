The median of medians algorithm achieves linear time for deterministic pivot selection. This allows you to optimise a quick sort by choosing a better pivot element which will more evenly divide the list into sublist for more efficient recursion. The algorithm works as follows:
1. Divide the list into groups of 5. Find the median of each group of 5 by rote.
2. Recursively select the median of medians as the pivot point for quicksort.
3. Partition around the pivot. Let k = rank(x)
4. if i = k then return 
5. if i < k then recursively select the i-th smallest element in the lower part.
6. else recursively select the (i - k)th element in the upper part