# Graphs

- Set of vertices pairwise joined by edges

## Undirected graphs

- `Adjacent(v,u)`: determines whether u and v are neighbors
- `Neighbors(v)`: return all neighbors of v
- `Insert(v,u)`: add edge(v,u) to G (unless is already there)



| Data structure   | Adjacent    | Neighbors | Insert | Plads    |
| ---------------- | ----------- | --------- | ------ | -------- |
| Adjacency matrix | $O(1)$      | $O(n)$    | $O(1)$ | $O(n^2)$ |
| Adjacency list   | $O(deg(v))$ | $O(deg(v))$ | $O(deg(v))$ | $O(n+m)$ |

## Directed graphs

- Application: Dependencies
- `PointsTo(u,v)` instead of `Adjecent(v,u)`

### DAGs (Directed acyclic graphs)
- Does not contain a cycle
### Strongly connected components
- Strongly connected - if there is a path `u` to `v` and a path `v` to `u`
- Strongly connected components - maximal subset of strongly connected vertices
# Algorithms on graphs

## Depth first search

- Algorithm for systematically visiting all vertices and edges
- Intuition:
  - Explore out from s in some direction, until coming to a "dead end"
  - Go back to the last place where there were unexplored edges. Repeat
  - Discover time. First time a vertex is visited
  - Finish time: Last time a vertex is visited
- Running time: $O(n+m)$ 

## Connected components

- How does one find all connected components?
- Algorithm:
  - Initially, let all vertices be unmarked
  - While there is an unmarked vertex
    - Chose an unmarked vertex v, run **DFS** from v
- Running time : $O(n + m)$ 

## Breadth first search

- Finds shortest paths and lengths from `s`
  - Distance to `s` in BFS tree = shortest distance to `s` in the original graph
- Paths is found by backtracking the parent of nodes
- Only vertices connected to s are visited
- Running time: $O(n +  m)$

## Bipartite graphs

- A graph is bipartite if and only if all cycles in G have even length
- Algorithm
  - Run **BFS** on G
  - For every edge of G, determine whether it goes between vertices of the same layer
- Running time:  $O( n + m )$

## Topological sorting of DAGs

- Idea
  - Run DFS on G
  - When returning from the recursive call on vertex v, push v to a stack
  - Print stack
## Strongly connected components via DFSes
- Idea
	- Run DFS on the reversed graph $G^R$
	- Note the finish times of all vertices
	- Run DFS on original G, but when starting a new "round", always start on the unmarked vertex with the highest finish-time
	- Each round finds and marks a strongly connected component