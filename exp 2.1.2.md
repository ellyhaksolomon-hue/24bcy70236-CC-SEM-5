# LeetCode 39: Combination Sum

## Problem Statement

Given an array of distinct integers `candidates` and a target integer `target`, return a list of all unique combinations of candidates where the chosen numbers sum to `target`.

You may select the same number from `candidates` an unlimited number of times.

Two combinations are considered unique if the frequency of at least one chosen number is different.

The combinations can be returned in any order.

### Example 1

**Input:**
```text
candidates = [2,3,6,7], target = 7
```

**Output:**
```text
[[2,2,3],[7]]
```

**Explanation:** The combinations `2 + 2 + 3 = 7` and `7 = 7` are the only valid combinations.

### Example 2

**Input:**
```text
candidates = [2,3,5], target = 8
```

**Output:**
```text
[[2,2,2,2],[2,3,3],[3,5]]
```

**Explanation:** These combinations contain numbers from the candidates array that sum to `8`.

### Example 3

**Input:**
```text
candidates = [2], target = 1
```

**Output:**
```text
[]
```

**Explanation:** No combination of `2` can produce the target value `1`.

## Solution (Python)

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        result = []
        path = []

        def backtrack(start, remaining):
            if remaining == 0:
                result.append(path.copy())
                return

            if remaining < 0:
                return

            for i in range(start, len(candidates)):
                path.append(candidates[i])

                # Reuse the same candidate if needed
                backtrack(i, remaining - candidates[i])

                path.pop()

        backtrack(0, target)
        return result
```

## Approach

The solution uses **backtracking** to find every unique combination that adds up to the target.

1. Initialize an empty list `result` to store valid combinations.
2. Create a temporary list `path` to store the current combination.
3. Define a recursive function `backtrack(start, remaining)`.
4. If `remaining` becomes `0`, copy the current combination into `result`.
5. If `remaining` becomes negative, stop exploring that path.
6. Iterate through the candidates starting from index `start`.
7. Add the current candidate to `path` and recursively search for the remaining sum.
8. Pass the same index `i` into the recursive call so that the candidate can be reused.
9. Remove the last candidate using `path.pop()` to explore other combinations.
10. Return `result` after all possible combinations have been explored.

Starting each recursive loop at the current index prevents duplicate combinations in different orders.

## Complexity Analysis

Let `N` be the number of candidates and `T` be the target.

### Time Complexity: Exponential

The algorithm explores multiple possible combinations through recursion. In the worst case, the number of recursive paths grows exponentially with the target and the smallest candidate value.

For positive integer candidates, a common upper-bound description is **O(N^(T/M + 1))**, where `M` is the smallest candidate. This is a loose bound; actual runtime depends on the candidates and the number of valid combinations.

### Space Complexity: O(T/M)

The recursion depth and temporary combination can grow to approximately `T/M`, where `M` is the smallest candidate. This excludes the space required to store the output.

The output list requires additional space proportional to the total size of all returned combinations.

## Key Concepts Learned

- Arrays and recursion
- Backtracking
- Depth-first search (DFS)
- Recursive state management
- Duplicate-combination prevention
- Time and space complexity analysis

## Conclusion

LeetCode 39: Combination Sum can be solved using backtracking by exploring possible candidate combinations and undoing each choice when exploring alternative paths. This approach finds all unique combinations that sum to the target while allowing candidates to be reused.
