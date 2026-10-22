# LeetCode 236: Lowest Common Ancestor of a Binary Tree

## Problem Statement

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in a tree that has both `p` and `q` as descendants, where a node can be a descendant of itself.”

### Example 1

**Input:**
```text
root = [3,5,1,6,2,0,8,null,null,7,4]
p = 5
q = 1
```

**Output:**
```text
3
```

**Explanation:** The lowest common ancestor of nodes `5` and `1` is node `3`, because both nodes are descendants of node `3`.

### Example 2

**Input:**
```text
root = [3,5,1,6,2,0,8,null,null,7,4]
p = 5
q = 4
```

**Output:**
```text
5
```

**Explanation:** The lowest common ancestor of nodes `5` and `4` is node `5`, because a node can be a descendant of itself.

### Example 3

**Input:**
```text
root = [1,2]
p = 1
q = 2
```

**Output:**
```text
1
```

**Explanation:** Node `1` is the lowest common ancestor of nodes `1` and `2`.

## Solution (Python)

```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        if root is None or root == p or root == q:
            return root

        left = self.lowestCommonAncestor(root.left, p, q)
        right = self.lowestCommonAncestor(root.right, p, q)

        if left and right:
            return root

        return left if left else right
```

## Approach

The solution uses **recursive Depth-First Search (DFS)** to locate the lowest common ancestor.

1. If the current node is `None`, return `None`.
2. If the current node matches either `p` or `q`, return that node.
3. Recursively search the left subtree for `p` and `q`.
4. Recursively search the right subtree for `p` and `q`.
5. If both recursive calls return non-null nodes, `p` and `q` were found in different subtrees. Therefore, the current node is their lowest common ancestor.
6. If only one side returns a non-null node, return that result.
7. Continue until the lowest common ancestor is identified.

The algorithm assumes both target nodes exist in the binary tree, as guaranteed by the original LeetCode problem.

## Complexity Analysis

Let `N` be the number of nodes in the binary tree and `H` be the height of the tree.

### Time Complexity: O(N)

In the worst case, the algorithm visits every node in the binary tree once.

Therefore, the time complexity is **O(N)**.

### Space Complexity: O(H)

The recursive calls use stack space proportional to the height of the tree.

- Balanced binary tree: `O(log N)`
- Skewed binary tree: `O(N)`

Therefore, the auxiliary space complexity is **O(H)**.

## Key Concepts Learned

- Binary trees
- Recursion
- Depth-First Search (DFS)
- Lowest Common Ancestor (LCA)
- Tree traversal
- Time and space complexity analysis

## Conclusion

LeetCode 236: Lowest Common Ancestor of a Binary Tree can be solved efficiently using recursive DFS. By searching both subtrees and combining their results, the algorithm identifies the lowest common ancestor in `O(N)` time with `O(H)` auxiliary space.
