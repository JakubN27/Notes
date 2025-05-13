## Array
A sequence of elements is called an array.
A string is an array of chars.

## Linked list
A list is made up of nodes. Each node contains an element and a pointer or link to the next node. The first node is called the head and the final node is called the tail.

### Traversing a Linked List
To find the ith element: 
- Start at the head node.
- Follow its pointer 
- Repeat i times
- Read the data in the node.

	In [[ADS Intro#Pseudocode| pseudocode]]: 
	
```
Input: list L, positive integer i  
	Output: ith piece of data in L  
	if i > L.size then  
		return out of range  
		end if  
	N = L.head  
	if i = 1 then  
		return N.data  
		end if  
	for j = 2 to i do  
		N = N.next  
		end for  
	return N.data
```

To alter the list, any predessecors or succesors must have their pointers altered appropriately.

Deletion of the head:
```
Input: list L  
Output: L with head deleted  

if L.head = NULL then  
	return no head to delete  
end if  
if L.head = L.tail then  
	L.head = NULL  
	L.tail = NULL  
	L.size = L.size - 1  
	return  
end if  
L.head = L.head.next  
L.size = L.size - 1
```
Insertion of **v** after **N**:
```
Input: list L, data v, node N  
Output: L with v inserted after N  
node M  
M.data = v  
M.next = N.next  
N.next = M  
if L.tail = N then  
	L.tail = M  
end if  
```

## Arrays versus Lists

| Operation           | [[#Array]] | [[#Linked list]] |
| ------------------- | :--------: | :--------------: |
| Data Access         |    fast    |       slow       |
| Insertion, Deletion |    slow    |       fast       |
## Doubly Linked Lists

A node in a doubly linked list stores two references:  
 - a next link, which points to the next node in the list  
 - a prev link, which points to the previous node in the list  
To simplify, we add two dummy or sentinel nodes at the ends of the doubly linked list:  
 - the header has a valid next reference but a null prev reference  
 - the tail has a valid prev reference but a null next reference  
A doubly linked list needs to store references to the two sentinel nodes and a size counter keeping track of the number of nodes in the list (not counting sentinels).  
An empty list would have the two sentinel nodes pointing to each other.

## Circularly Linked List

Has the same kind of nodes as a singularly linked list, but it has on beginning and no end. The final next pointer points back to the first node. Instead of references to the head and the tail, we mark a node of  the circularly linked list as the cursor. The cursor is the starting  node when we traverse the list.  

Deletion from a doubly linked list:
```
Input: list L, node N  
Output: L with N removed  
M = N.prev  
P = N.next  
M.next = P  
P.prev = M  
L.size = L.size - 1
```