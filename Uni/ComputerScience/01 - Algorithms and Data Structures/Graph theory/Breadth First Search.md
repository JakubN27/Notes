Breadth First Search (BFS) is a graph traversal algorithm that explores all nodes at the current level of a graph before moving down to the level. Closest vertices are visited before others.
Iterative implementation:
```
BFS(graph, root)
	let Q be a queue
	label root as explored
	Q.enqueue(root)
	while Q is not empty do
		v = Q.dequeue()
		if v is the goal then
			return v
		for all edges from v to w in G.adjacentedges(v) do
			label w as explored
			w.parent = v
			Q.enqueue(w)
```
This is similar to the iterative implementation of the [[Depth First Search]], however it uses a [[Queues|queue]] instead of a [[Stacks|stack]] and it checks whether a vertex has been explored before enqueueing the vertex rather than delaying this check until the vertex is dequeued from the queue

# Breadth first tree
The graph obtained from the edges used to discover new vertices forms a tree called the breadth-first tree. The path from the root to any node in the tree is the shortest path 