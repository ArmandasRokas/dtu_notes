# Data structures

- Method for organizing data for efficient access, searching

- **Goal**: Fast and compact
- Abstract vs concrete
- Dynamic vs static

## Stack

- Dynamic sequence. *last-in first-out*
- Supports `push(x)`, `pop()`, `isEmpty`

## Queue

- Dynamic sequence. *first-in first-out*
- Supports `enqueue(x)`, `dequeue()`, `isEmpty()`

## Linked-list

- Dynamic sequence of elements in linear space
- `Search` in $\Theta(n)$
- `Insert` and `Delete` in $\Theta(1)$
- Space $\Theta(n)$


## Trees

- Special type of graph
- Connect and acyclic
- Designated root node
- Binary trees
  - Two children

## Heaps

- Almost complete binary tree that satisfies **heap-order**:
  - All nodes store one element
  - For all nodes `v`:
    - all keys in left subtree and right subtree are <= `v.key`

### Build a heap
- Given n integers in a array convert to a heap
- bottom-up construction
  - Apply BubbleDown
- $O(n)$

### Array representation
- `Parent(x)`: return x/2
- `Left(x)`: return 2x
- `Right(x)`: return 2x+1
### Algorithm on heaps
- `BubbleUp(x)`
- `BubbleDown(x)`
- Running time: $O(\log{}n)$

### Priority queues with heaps

- Maintain dynamic set S supporting the following operations. Each element has key `x.key` and satellite data `x.data`
- `Max()`: return element med largest key
  - return first elements
  - $O(1)$
- `ExtractMax()`: return and remove element with largest key
  - uses `BubbleDown`
  - $O( \log{}n)$
- `IncreaseKey(x,k)`: set `x.key` = `k` 
  - uses `BubbleUp`
  - $O( \log{}n)$
- `Insert(x)`
  - uses `BubbleUp`
  - $O( \log{}n)$

### Heapsort

- Heap construction 
- Apply `n` `ExtractMax`
- Running time: $O(n\log{}n)$

## Union Find

- Maintain a dynamic family of sets supporting the following operations:
  - `Init(n)` : construct sets
  - `Union(i,j)`: forms the union of the two sets that contains `i` and `j`. If `i` and `j` are in the same set nothing happpens
  - `Find(i)`: return a representative for the set that contains `i`

| Data structure                             | Union         | Find         |
| ------------------------------------------ | ------------- | ------------ |
| quick find                                 | $O( n )$      | $O( 1 )$     |
| quick union                                | $O(n)$        | $O( n )$     |
| weighted quick union with path compression | $O(\log{} n)$ | $O(\log n )$ |

## Dynamic Connectivity

- Maintain a dynamic graph supporting the following operations:
  - `Init(n)` : creates a graph G med n vertices and no edges
    - $O ( n ) $
  - `Connected(u,v)`: determine if `u` and `v` are connected
    - `Find(u)` == `Find(v)`
    - $ O( \log{} n  ) $
  - `Insert(u,v)`: add edge (u,v). We assume (u,v) does not exists
    - `Union(u,v)`
    - $O( \log{} n )$