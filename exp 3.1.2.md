# LeetCode 403: Frog Jump

## Problem Statement

A frog is crossing a river. The river is divided into units, and some units contain stones.

The frog can jump onto a stone, but it must start on the first stone at position `0`. The frog's first jump must be exactly `1` unit.

If the frog's last jump was `k` units, its next jump must be either `k - 1`, `k`, or `k + 1` units. The frog can only jump forward, so every jump must have a positive length.

Given an array `stones` representing the positions of stones in ascending order, return `true` if the frog can cross the river by landing on the last stone. Otherwise, return `false`.

### Example 1

**Input:**
```text
stones = [0,1,3,5,6,8,12,17]
```

**Output:**
```text
true
```

**Explanation:** The frog can cross the river by jumping to positions `1`, `3`, `5`, `8`, `12`, and `17`.

The jump lengths are `1, 2, 2, 3, 4, 5`.

### Example 2

**Input:**
```text
stones = [0,1,2,3,4,8,9,11]
```

**Output:**
```text
false
```

**Explanation:** The gap between positions `4` and `8` is too large for the frog to reach position `8` under the jump rules.

## Solution (Python)

```python
class Solution:
    def canCross(self, stones: List[int]) -> bool:
        if stones[1] != 1:
            return False

        stone_set = set(stones)
        target = stones[-1]
        memo = {}

        def dfs(position, last_jump):
            if position == target:
                return True

            if (position, last_jump) in memo:
                return memo[(position, last_jump)]

            for jump in (last_jump - 1, last_jump, last_jump + 1):
                if jump > 0 and position + jump in stone_set:
                    if dfs(position + jump, jump):
                        memo[(position, last_jump)] = True
                        return True

            memo[(position, last_jump)] = False
            return False

        return dfs(0, 0)
```

## Approach

The solution uses **Depth-First Search (DFS) with memoization** to determine whether the frog can reach the last stone.

1. Check whether the second stone is at position `1`. If not, return `False`, because the frog's first jump must be exactly one unit.
2. Convert the stone positions into a set for efficient membership checks.
3. Use a recursive function `dfs
