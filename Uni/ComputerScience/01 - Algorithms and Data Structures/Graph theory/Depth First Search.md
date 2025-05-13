Depth-First Search (DFS) is an algorithm for traversing or searching tree or graph data structures. It follows a branch in its entirety before backtracking and trying another branch.
```
DFS(Graph, v)
	let S be a stack
	S.push(v)
	while S is not empty do
		v = S.pop()
		if v is not labeled as visited then
			label v as visited
			for each vertex w in Graph.adjacentedges(v)
				S.push(w)
```

Recursive approach:
```
DFS(Graph, v)
	visited[v] = True
	print v
	for each vertex w in Graph.adjacentedges(v)
		if visited[w] == False
			DFS(Graph, w)
```
When a vertex is discovered it is immediately explored. Two timestamps are recorded for each vertex, d and f for when they are discovered and when they are finished. We can also record predecessors again. We increment the 'time' or number of steps each time.