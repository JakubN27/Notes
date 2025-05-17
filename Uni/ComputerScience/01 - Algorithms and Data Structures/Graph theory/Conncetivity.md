# Paths
A walk in a graph G is a sequence of edges $v_0, v_1, v_2 ... v_{n-1}, v_n$. A path is a walk if all edges are distinct. A path is called a circuit if $v_0 = v_n$. A circuit is called a cycle if all edges are distinct. 

## Eulerian Cycle
A Eulerian Cycle is a cycle where you start and end at the same vertex and hit every edge exactly once.

## Hamiltonian Cycle
A Hamiltonian cycle is a cycle where you start and end at the same vertex and hit every vertex once. 

# Connected Components
A graph is **connected** if between every pair of vertices *u, v* there exists at least one path in G.
A connected component of G is a maximal connected subgraph of G.

## Strong connectivity
A directed graph G is called weakly connected if the graph obtained from G by forgetting directions is connected.
A directed graph is called strongly directed if and two distinct vertices are connected by directed paths in both directions. 
A strongly connected component of a digraph G is a maximal strongly connected subgraph of G.
