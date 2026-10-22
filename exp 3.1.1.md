# LeetCode 70: Climbing Stairs

## Problem Statement

You are climbing a staircase. It takes `n` steps to reach the top.

Each time, you can either climb `1` step or `2` steps. In how many distinct ways can you climb to the top?

### Example 1

**Input:**
```text
n = 2
```

**Output:**
```text
2
```

**Explanation:** There are two ways to climb to the top:
- `1 step + 1 step`
- `2 steps`

### Example 2

**Input:**
```text
n = 3
```

**Output:**
```text
3
```

**Explanation:** There are three ways to climb to the top:
- `1 step + 1 step + 1 step`
- `1 step + 2 steps`
- `2 steps + 1 step`

## Solution (Python)

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n <= 2:
            return n

        first = 1
        second = 2

        for i in range(3, n + 1):
            current = first + second
            first = second
            second = current

        return second
```

## Approach

The solution uses **Dynamic Programming** with an optimized space approach.

To reach step `n`, you can arrive from either:
- Step `n - 1` by taking one step.
- Step `n - 2` by taking two steps.

Therefore, the recurrence relation is:

`dp[n] = dp[n - 1] + dp[n - 2]`

### Steps

1. If `n` is `1` or `2`, return `n` directly.
2. Initialize `first = 1` and `second = 2`.
3. Starting from step `3`, calculate the current number of ways by adding the previous two values.
4. Update the two variables to keep track of the previous results.
5. Repeat until reaching step `n`.
6. Return `second`, which contains the total number of ways.

This approach avoids storing an entire dynamic programming array.

## Complexity Analysis

### Time Complexity: O(N)

The algorithm uses a single loop from step `3` to step `n`. Each iteration performs a constant number of operations.

Therefore, the time complexity is **O(N)**.

### Space Complexity: O(1)

The algorithm uses only three variables: `first`, `second`, and `current`. It does not require an additional array.

Therefore, the auxiliary space complexity is **O(1)**.

## Key Concepts Learned

- Dynamic programming
- Fibonacci sequence
- Recurrence relations
- Iteration
- Space optimization
- Time and space complexity analysis

## Conclusion

LeetCode 70: Climbing Stairs can be solved using dynamic programming by calculating each result from the previous two results. The optimized solution runs in `O(N)` time and uses `O(1)` auxiliary space.
