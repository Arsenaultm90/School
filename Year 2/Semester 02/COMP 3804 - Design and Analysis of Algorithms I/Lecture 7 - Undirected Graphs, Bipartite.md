$G = (V, E)$
	V : Set of vertices
	E : Set of edges

Undirected : edge {u, v}
Directed : edge (u, v)

![[Drawing 2026-02-11 08.05.57.excalidraw]]


Degree(u) : Number of edges that have $'u'$ as a vertex.

Note :
	Number of edges is always even


---
# Adjacency Matrix

An **adjacency matrix** represents a graph using a 2D array.

For a graph $G = (V, E)$ with $|V| = n$

We create an $n \times n$ matrix $M$ where:
$$M[i][j] = \begin{cases} 1 & \text{if there is an edge from } i \text{ to } j \\ 0 & \text{otherwise} \end{cases}$$
If the graph is weighted:
$$M[i][j] = \begin{cases} \text{weight of edge } (i,j) & \text{if edge exists} \\ 0 \text{ or } \infty & \text{if no edge} \end{cases}$$

Space Complexity : $O(n^2)$
Constant time edge lookup

**Example : Undirected Graph**
Vertices: {1,2,3,4}
Edges:
- (1,2)
- (1,3)
- (2,4)

Adjacency Matrix:
```
     1  2  3  4
   ----------------
1 |  0  1  1  0
2 |  1  0  0  1
3 |  1  0  0  0
4 |  0  1  0  0
```



---
# Adjacency Lists

An **adjacency list** represents a graph by storing, for each vertex:
	A list of its neighbours.

Instead of an $n \times n$ matrix, we store:
```
Vertex 1 → [neighbors of 1]
Vertex 2 → [neighbors of 2]
...
Vertex n → [neighbors of n]
```

Space Complexity : $O(n + m)$
Edge Lookup : $O(deg(u))$

**Example : Undirected Graph**
Vertices: {1,2,3,4}
Edges:
- (1,2)
- (1,3)
- (2,4)

Adjacency list:
```
1: 2, 3
2: 1, 4
3: 1
4: 2
```



---
# Depth First Search

DFS explores a graph by going **as deep as possible** along each branch before backtracking.

**Recursive Algorithm :**
```
DFS(G):
    mark all vertices as unvisited
    for each vertex u in G:
        if u is unvisited:
            DFS-Visit(u)

DFS-Visit(u):
    mark u as visited
    for each neighbor v of u:
        if v is unvisited:
            DFS-Visit(v)
```


**Example :** 
![[Drawing 2026-02-11 08.25.02.excalidraw|1000]]



---
# Bipartite Graphs

A graph is **bipartite** if:
	Its vertices can be split into two sets L and R such that **every edge connects a vertex in L to a vertex in R**.

**Properties :**
- No odd-length cycle
- Chromatic number ≤ 2
- Can partition into two independent sets
- Maximum matching problems are often defined on bipartite graphs


![[Excalidraw/Drawing 2026-02-11 12.49.00.excalidraw.md|200]]

Testing Bipartite : $O(|V| + |E|)$

