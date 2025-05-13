# Graph
A graph G is a pair (V(G), E(G)), where V(G) is a nonempty set of vertices(or nodes) and E(G) is a set of unordered pairs {u, v} with $u,v\in V(G)$ and u is not the same as v, called the edges of G.
- V(G) can be infinite.
- May see uv instead of {u, v}
- If the graph G is clear from the context, we write V and R instead of V(G) and E(G)

# Terminology
Let G be a graph and uv an edge in it. Then:
- u and v are called endpoints of the edge uv
- u and v are called neighbours or adjacent vertices
- uv is said to be incident to u and to v 
- is vw is also an edge (where w is not v) then uc and vw are called adjacent

Let G = (V, E) be a graph. The neighbourhood of a vertex $v \in V$, notation N(v), is the set of neighbours of v, i.e., N(v) = ${n \in V | uv \in E}$ The degree of a vertex $v \in V$, notation deg(v) is the number of neighbours of v = |N(v)|. With $\delta$(G) or $\delta$ we denote the smallest degree in G and with $\Delta$(G) or $\Delta$ the largest degree. A vertex with degree p will be called an isolated vertex. A vertex with degree 1 an end vertex or a pendant vertex.

The diameter of a graph is the largest distance between two vertices in it.