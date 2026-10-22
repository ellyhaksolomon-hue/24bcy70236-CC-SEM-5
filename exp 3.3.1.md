# LeetCode 200: Number of Islands

## Problem Statement

You are given an `m x n` 2D binary grid `grid` consisting of `'1'` (land) and `'0'` (water).

An island is formed by connecting adjacent land cells horizontally or vertically. You may assume that the grid is surrounded by water.

Return the number of islands in the grid.

### Example 1

**Input:**
```python
grid = [
    ["1", "1", "1", "1", "0"],
    ["1", "1", "0", "1", "0"],
    ["1", "1", "0", "0", "0"],
    ["0", "0", "0", "0", "0"]
]
```

**Output:**
```python
1
```

**Explanation:**

All the connected land cells form one island.

### Example 2

**Input:**
```python
grid = [
    ["1", "1", "0", "0", "0"],
    ["1", "1", "0", "0", "0"],
    ["0", "0", "1", "0", "0"],
    ["0", "0", "0", "1", "1"]
]
```

**Output:**
```python
3
```

**Explanation:**

There are three separate islands in the grid.

---

## Python Solution

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid:
            return 0

        rows = len(grid)
        cols = len(grid[0])
        islands = 0

        def dfs(r, c):
            if (
                r < 0 or r >= rows or
                c < 0 or c >= cols or
                grid[r][c] == "0"
            ):
                return
