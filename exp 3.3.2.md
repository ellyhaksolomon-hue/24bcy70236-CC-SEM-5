# LeetCode 1971: Find if Path Exists in Graph

## Problem Statement

There is a **bi-directional graph** with `n` vertices labeled from `0` to `n - 1`. The graph is represented by a 2D integer array `edges`, where each `edges[i] = [u, v]` indicates an edge between vertex `u` and vertex `v`.

Each vertex may be connected to multiple other vertices, and there are no edges from a vertex to itself or duplicate edges.

You are given two integers, `source` and `destination`.

Return `true` if there is a valid path from `source` to `destination`, or `false` otherwise.

### Example 1

**Input:**
```python
n = 3
edges = [[0, 1], [1, 2], [2, 0]]
source = 0
destination = 2
```

**Output:**
```python
True
```

**Explanation:**

There is a path from vertex `0` to vertex `2`, such as `0 → 2`.

### Example 2

**Input:**
```python
n = 6
edges = [[0, 1], [0, 2], [3, 5], [5, 4], [4, 3]]
source = 0
destination = 5
```

**Output:**
```python
False
```

**Explanation:**

Vertices `0` and `5` belong to separate connected components, so no path exists between them.

---

## Python Solution

```python
class Solution:
    def validPath(
        self,
        n: int,
        edges: List[List[int]],
        source: int,
        destination: int
    ) -> bool:
        graph = [[] for _ in range(n)]

        for u, v in edges:
            graph[u].append(v)
            graph[v].append(u)

        visited = set()
        stack = [source]

        while stack:
            node = stack.pop()

            if node == destination:
                return True

            if node in visited:
                continue

            visited.add(node)

            for neighbor in graph[node]:
                if neighbor not in visited:
                    stack.append(neighbor)

        return False
```

---

## Approach: Depth-First Search (DFS)

We use **Depth-First Search (DFS)** to determine whether a path exists between the source and destination vertices.

### Step 1: Build the Graph

Create an adjacency list using `n` empty lists.

For every edge `[u, v]`, add `v` to the neighbors of `u` and `u` to the neighbors of `v`. Since the graph is bidirectional, both directions must be included.

### Step 2: Initialize the Search

- `visited` stores the vertices already explored.
- `stack` stores the vertices waiting to be explored.
- Start the search by placing `source` in the stack.

### Step 3: Explore the Graph

While the stack is not empty:

1. Remove a vertex from the stack.
2. If it equals `destination`, return `True`.
3. If it has already been visited, skip it.
4. Otherwise, mark it as visited and add its unvisited neighbors to the stack.

### Step 4: Return the Result

If the stack becomes empty before reaching the destination, return `False`. This means no path exists between the two vertices.

---

## Complexity Analysis

Let `n` be the number of vertices and `m` be the number of edges.

### Time Complexity

**O(n + m)**

Building the adjacency list takes `O(n + m)` time, and DFS visits each vertex and explores each edge at most a constant number of times.

### Space Complexity

**O(n + m)**

The adjacency list requires `O(n + m)` space. The visited set and stack require up to `O(n)` additional space.

---

## Key Concepts

- Graphs
- Adjacency lists
- Depth-First Search (DFS)
- Stack
- Visited set
- Graph connectivity

---

## Conclusion

LeetCode 1971, Find if Path Exists in Graph, is a graph traversal problem. By representing the graph as an adjacency list and using DFS, we can efficiently determine whether the destination is reachable from the source.

**Time Complexity:** `O(n + m)`

**Space Complexity:** `O(n + m)`
