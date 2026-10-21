# LeetCode 35: Search Insert Position

## Problem Statement

Given a sorted array of distinct integers `nums` and a target value `target`, return the index if the target is found. If not, return the index where the target would be inserted in order to maintain the array's sorted order.

You must write an algorithm with `O(log N)` runtime complexity.

### Example 1

**Input:**
```text
nums = [1,3,5,6], target = 5
```

**Output:**
```text
2
```

**Explanation:** The target `5` is found at index `2`.

### Example 2

**Input:**
```text
nums = [1,3,5,6], target = 2
```

**Output:**
```text
1
```

**Explanation:** The target `2` should be inserted at index `1` to maintain sorted order.

### Example 3

**Input:**
```text
nums = [1,3,5,6], target = 7
```

**Output:**
```text
4
```

**Explanation:** The target `7` should be inserted at the end of the array, at index `4`.

## Solution (Python)

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums) - 1

        while left <= right:
            mid = (left + right) // 2

            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1

        return left
```

## Approach

The solution uses **Binary Search** because the input array is sorted.

1. Initialize `left` to `0` and `right` to the last index of the array.
2. Calculate the middle index using `(left + right) // 2`.
3. If `nums[mid]` equals the target, return `mid`.
4. If `nums[mid]` is less than the target, search the right half by updating `left = mid + 1`.
5. If `nums[mid]` is greater than the target, search the left half by updating `right = mid - 1`.
6. If the target is not found, return `left`, which represents the correct insertion position.

## Complexity Analysis

### Time Complexity: O(log N)

Binary search eliminates approximately half of the remaining search space in every iteration. Therefore, the time complexity is `O(log N)`, where `N` is the length of the array.

### Space Complexity: O(1)

The algorithm uses only a constant number of extra variables: `left`, `right`, and `mid`. It does not create another array, so the auxiliary space complexity is `O(1)`.

## Key Concepts Learned

- Arrays
- Binary search
- Sorted arrays
- Index manipulation
- Time and space complexity analysis

## Conclusion

LeetCode 35: Search Insert Position can be solved efficiently using binary search. The algorithm finds the target index or its correct insertion position in `O(log N)` time and `O(1)` auxiliary space.
