# Binary Search
When searching for an element in a list, assuming the list is sorted we can use a binary search.
In a binary search:
- We take the middle element of the sorted list and compare it to the value we are looking for.
- If it is larger treat all the elements to the right as a sublist 
- Recurse on the sublist until the value is found.
- Time complexity o(logn)

# Quick-search
Quick search is like the quick sort equivalent of searching. It is recursive, uses a partition function to split up the list to parts bigger and smaller than the pivot. It varies from quicksort in the way there is only one recursive call rather than two, since we know that the pivot element will be in the correct position with respect to the sorted version which we dont have yet. I.e. if there are 4 elements to the right of the pivot, in any order, we know we have the 5th highest element.

In the worst case, where all the elements are already sorted and we pick the right most element as the pivot every time, the algorithm is O($n^{2}$), which is worse than just mergesorting the list and picking the i-th element.

However, if the index of the pivot element is randomised (within the current subproblem), the expected running time is O(n), although there is still a tiny chance it may run in O($n^2$) time.

Like quicksort, quick-select can be optimised using [[Median of Medians]]. 

