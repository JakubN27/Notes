A hash table consists of a bucket array and a [[#Hash Functions]] A bucket array for a has table is an array A of size N where each cell of A is thought as a bucket storing a collection of key-value pairs.
The size N of the array is called the capacity of the hash table.
The hash function g is a function mapping each key k to an integer in the range [0, N-1], where N is the capacity of the hash table. The main idea is to use h(k) as an index into the bucket array A. That is, we store the kay-value pair (k, v) in the bucket A[h(k)]. If there are two keys with the same has value h(k), then two different entries will try to map to the same bucket in A. This is known as a [[#Collision]].

## Hash Function

A hash function is usually specified as the composition of two functions:
 - hash code: keys to integers
 - compression function: integers to [0, N-1]
The hash code is applied first and the compression function is applied next on the result. 
The goal of the hash function is to disperse the keys in an apparently random way and in a uniform way.
Each has function should be:
- Efficiently computable
- Each table position should be equally likely for each key.
Some compression functions include: 
- division: take integer mod N
- multiply add and divide (MAD): y maps to (ay + b mod N) where a and b are nonnegative integers.
## Collision

A large number of collisions reduces the performance of the hash table. A good hash function minimises the number of collisions as much as possible, but it is impossible to avoid them completely, so they must be dealt with.

The four main ways of handling collisions are:
- [[#Separate chaining]].
- [[#Linear probing]].
- [[#Quadratic probing]].
- [[#Double hashing]].

### Separate chaining
Each bucket A[i] stores a list holding the entries (k, v) such that h(k) = i.
- Cost is proportional to length of list.
- Average length = N/M (N is the amount of data, M is the size of the array)
- Worst case: all keys has to the same list.
The other three methods, called open addressing schemes, store at most one entry to each bucket.
### Linear probing
- In linear probing if we try to insert an entry (k, v) into a bucket A[i] that is already occupied, where i = h(k), then we try next at A[(i + 1) mod N]
- If A[(i + 1) mod N] is also occupied, then we try A[(i + 2) mod N] and so on, until we find an empty bucket that can accept the new entry.
- Essentially, try the next cell in the bucket until it is free.
- Insert and search cost depend on the length of the cluster
- Average length of cluster is N/M
- Worst case: all keys hash to the same cluster.
### Quadratic probing
- Quadratic probing iteratively tries the buckets A[(i + f(j)) mod N] for j = 0, 1, 2, ... , where f(j) = j^2 until finding an empty bucket.
- Quadratic probing avoids clustering patterns that occur with linear probing. However, it creates its own kind of clustering, called secondary clustering.
- The quadratic probing strategy may not find an empty bucket in A even if one exists.
### Double hashing
- In this approach, we choose a secondary has function, *h'* , and if h maps some key k to a bucket A[i], with i = h(k), that is already occupied, then we iteratively try the buckets: A[(i + f(j)) mod N], for j = 0, 1, 2, ... , where f(j) = j * h'(k).
- A common choice of secondary hash function is h'(k) = q - (k mod q). for some prime number q < N. 
- The secondary hash function should not evaluate to zero.

### Comparison
- The open addressing schemes are more memory efficient compared to separate chaining. 
- Regarding running times, in experimental and theoretical analyses, the separate chaining method is either competitive or faster than the other methods.
- If memory space is not a major issue, the collision-handling method of choice is separate chaining.

## Deletions
- Deletions from the hash table must not hinder future searches. If a bucket is simply left empty this will hinder future probes. But the bucket should not be left unusable.
- To solve these problems we use *tombstones*: a market that is left in a bucket after a deletion.
- If a tombstone is encountered when searching along a probe sequence to find a key, we know to continue.
- If a tombstone is encountered during insertion, then we should continue probing (to avoid creating duplicates), but then the new record can be placed in the bucket where the tombstone was found.
- The use of tombstones lengthens the average probe sequence distance.
- Two possible remedies:
	-  Local reorganisation: after deleting a key, continue to follow the probe sequence of that key and move records into the vacated bucket.
	- Periodically rehash the table by reinserting all records into a new hash table. And if you have a record of which keys are accessed most of these can be played where they will be found most easily.
