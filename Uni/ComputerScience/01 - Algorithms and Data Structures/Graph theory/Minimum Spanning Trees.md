An algorithm finds a spanning connected subgraph, aka the cheapest way to connect all nodes without cycles. The sum of weights of all edges should be the smallest possible. It is impossible for the solution to contain a cycle, since it would be cheaper to remove one of the edges, therefore it will always result in a tree.

# Kruskal's Algorithm
 Repeatedly add the next cheapest edge that does not produce a cycle.

```
 MST(Graph):
	 MST = {}
	 sort all edges by their weight in a list L
	 for each edge e in L
		 if (MST + e) contains no cycle then
			 MST = MST + e
	return MST
```

Kruskal's algorithm will find the minimum spanning tree of an unconnnected graph. It does not work on a node by node basis, but takes the cheapest edges which do not lead to a cycle, until all possible nodes are connected.

# Prim's Algorithm
Prim's Algorithm finds the MST of a connected and undirected graph. It works by first adding a random node to the MST. It then compares all edges connected to the current MST and follows the cheapest one, adding this edge and the connecting node to the MST
```
MST(Graph)
	MST = {}
	current_node = Graph[0]
	MST += current_node
	edges = current_node.edges
	while size(MST) < size(Graph)
		minEdge = min(edges)
		MST += minEdge
		for edge in edges connected to minEdge
			if edge is not in MST
				edges.add(edge)
		edges.remove(minEdge)
	return MST
```