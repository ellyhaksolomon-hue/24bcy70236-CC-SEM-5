# LeetCode 219: Contains Duplicate II

## Problem Statement

Given an integer array `nums` and an integer `k`, return `true` if there are two distinct indices `i` and `j` in the array such that:

- `nums[i] == nums[j]`
- `abs(i - j) <= k`

Otherwise, return `false`.

In simple words, determine whether the array contains two equal elements whose indices are at most `k` positions apart.

### Example 1

**Input:**
```text
nums = [1,2,3,1], k = 3
```

**Output:**
```text
true
```

**Explanation:** The elements at indices `0` and `3` are both `1`, and their index difference is `3`, which is equal to `k`.

### Example 2

**Input:**
```text
nums = [1,0,1,1], k = 1
```

**Output:**
```text
true
```

**Explanation:** The elements at indices `2` and `3` are both `1`, and their index difference is `1`.

### Example 3

**Input:**
```text
nums = [1,2,3,1,2,3], k = 2
```

**Output:**
```text
false
```

**Explanation:** No two equal elements occur within a distance of `2` indices.

## Solution (Python)

```python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        seen = {}

        for i, num in enumerate(nums):
            if num in seen and i - seen[num] <= k:
                return True

            seen[num] = i

        return False
```

## Approach

1. Create a dictionary named `seen` to store each number and its most recent index.
2. Traverse the array using `enumerate()` to obtain each element and its index.
3. Check whether the current number already exists in the dictionary.
4. If it exists and the difference between the current index and its stored index is less than or equal to `k`, return `True`.
5. Otherwise, update the dictionary with the current index.
6. If no valid pair is found after traversing the array, return `False`.

## Complexity Analysis

### Time Complexity: O(N)

The algorithm traverses the array once. Dictionary lookups and updates take O(1) average time, so the overall average time complexity is O(N), where N is the length of the array.

### Space Complexity: O(N)

In the worst case, the dictionary stores up to N distinct elements and their indices. Therefore, the auxiliary space complexity is O(N).

## Conclusion

LeetCode 219: Contains Duplicate II can be solved efficiently using a dictionary to track the most recent index of each element. This approach avoids unnecessary nested loops and achieves O(N) average time complexity with O(N) auxiliary space complexity.
