# LeetCode 258: Add Digits

## Problem Statement

Given an integer `num`, repeatedly add all its digits until the result has only one digit, and return that one-digit result.

You must solve the problem without using any loop or recursion and in `O(1)` runtime complexity.

### Example 1

**Input:**
```text
num = 38
```

**Output:**
```text
2
```

**Explanation:**

The process is:

- `3 + 8 = 11`
- `1 + 1 = 2`

Since `2` is a single digit, the answer is `2`.

### Example 2

**Input:**
```text
num = 0
```

**Output:**
```text
0
```

**Explanation:** The number `0` already has only one digit, so the result is `0`.

## Solution (Python)

```python
class Solution:
    def addDigits(self, num: int) -> int:
        if num == 0:
            return 0

        return 1 + (num - 1) % 9
```

## Approach

The solution uses a mathematical technique called the **Digital Root**.

Instead of repeatedly adding the digits using loops, we can calculate the result directly using the following formula:

`Digital Root = 1 + (num - 1) % 9`, for positive integers.

Steps:

1. Check whether `num` is `0`. If it is, return `0`.
2. For positive integers, subtract `1` from `num`.
3. Calculate the remainder when the result is divided by `9`.
4. Add `1` to the remainder.
5. Return the final single-digit result.

This formula works because the digital root of a positive integer follows a repeating pattern based on its remainder modulo `9`.

## Complexity Analysis

### Time Complexity: O(1)

The solution uses a fixed number of arithmetic operations, regardless of the size of the input number.

Therefore, the time complexity is **O(1)**.

### Space Complexity: O(1)

The algorithm uses only a constant amount of extra space and does not create any additional data structures.

Therefore, the auxiliary space complexity is **O(1)**.

## Key Concepts Learned

- Mathematical operations
- Modulo operator (`%`)
- Digital root
- Number theory
- Constant-time algorithms
- Time and space complexity analysis

## Conclusion

LeetCode 258: Add Digits can be solved efficiently using the digital root formula. This mathematical approach eliminates the need for loops and recursion, achieving `O(1)` time complexity and `O(1)` auxiliary space.
