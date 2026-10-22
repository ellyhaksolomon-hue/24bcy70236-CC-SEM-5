# LeetCode 1143: Longest Common Subsequence

## Problem Statement

Given two strings, `text1` and `text2`, return the length of their **longest common subsequence**.

A subsequence is a sequence of characters that can be obtained from a string by deleting some characters without changing the order of the remaining characters.

A common subsequence must appear in both strings in the same relative order, but the characters do not need to be next to each other.

If the two strings have no common subsequence, return `0`.

### Example 1

**Input:**
```python
text1 = "abcde"
text2 = "ace"
```

**Output:**
```python
3
```

**Explanation:**

The longest common subsequence is `"ace"`, which has a length of `3`.

### Example 2

**Input:**
```python
text1 = "abc"
text2 = "abc"
```

**Output:**
```python
3
```

**Explanation:**

The longest common subsequence is `"abc"`, which has a length of `3`.

### Example 3

**Input:**
```python
text1 = "abc"
text2 = "def"
```

**Output:**
```python
0
```

**Explanation:**

The two strings have no common characters, so the answer is `0`.

---

## Python Solution

```python
class Solution:
    def longestCommonSubsequence(self, text1: str, text2: str) -> int:
        m = len(text1)
        n = len(text2)

        dp = [[0] * (n + 1) for _ in range(m + 1)]

        for i in range(1, m + 1):
            for j in range(1, n + 1):
                if text1[i - 1] == text2[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1] + 1
                else:
                    dp[i][j] = max(
                        dp[i - 1][j],
                        dp[i][j - 1]
                    )

        return dp[m][n]
```

---

## Approach: Dynamic Programming

We use **Dynamic Programming (DP)** to find the longest common subsequence of the two strings.

### Step 1: Create a DP Table

Create a two-dimensional array `dp` with `(m + 1)` rows and `(n + 1)` columns, where:

- `m` is the length of `text1`.
- `n` is the length of `text2`.
- `dp[i][j]` represents the length of the longest common subsequence between the first `i` characters of `text1` and the first `j` characters of `text2`.

Initially, every value is `0`, because an empty string has no common subsequence with any string.

### Step 2: Compare the Characters

For every character in both strings:

- **If the characters match:** Add `1` to the result from the previous diagonal cell.

  `dp[i][j] = dp[i - 1][j - 1] + 1`

- **If the characters do not match:** Take the maximum value from the cell above or the cell to the left.

  `dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])`

### Step 3: Return the Answer

After filling the table, return `dp[m][n]`, which contains the length of the longest common subsequence of the two complete strings.

---

## Complexity Analysis

Let `m` be the length of `text1` and `n` be the length of `text2`.

### Time Complexity

**O(m × n)**

We compare characters using two nested loops, processing each cell of the DP table once.

### Space Complexity

**O(m × n)**

We store the results in a two-dimensional DP table containing `(m + 1) × (n + 1)` cells.

---

## Key Concepts

- Dynamic Programming
- Two-dimensional arrays
- String comparison
- Subsequences
- Optimal substructure

---

## Conclusion

LeetCode 1143, Longest Common Subsequence, uses Dynamic Programming to find the longest sequence of characters shared by two strings while preserving their order.

The solution compares characters and builds the answer using previously calculated results.

**Time Complexity:** `O(m × n)`

**Space Complexity:** `O(m × n)`
