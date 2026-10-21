# LeetCode 238: Product of Array Except Self

## Problem Statement

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.

**Important:** You must write an algorithm that runs in `O(N)` time and does not use the division operation.

### Example 1

**Input:**
```text
nums = [1,2,3,4]
```

**Output:**
```text
[24,12,8,6]
```

**Explanation:**
- `answer[0] = 2 × 3 × 4 = 24`
- `answer[1] = 1 × 3 × 4 = 12`
- `answer[2] = 1 × 2 × 4 = 8`
- `answer[3] = 1 × 2 × 3 = 6`

### Example 2

**Input:**
```text
nums = [-1,1,0,-3,3]
```

**Output:**
```text
[0,0,9,0,0]
```

**Explanation:** Since the array contains zero, the products for indices other than the zero's index are zero. At index `2`, excluding the zero leaves `(-1) × 1 × (-3) × 3 = 9`.

## Solution (Python)

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        answer = [1] * n

        # Calculate products of all elements to the left
        prefix = 1
        for i in range(n):
            answer[i] = prefix
            prefix *= nums[i]

        # Multiply by products of all elements to the right
        suffix = 1
        for i in range(n - 1, -1, -1):
            answer[i] *= suffix
            suffix *= nums[i]

        return answer
```

## Approach

The solution uses the **prefix and suffix product technique**.

1. Initialize an `answer` array with all elements set to `1`.
2. Traverse the array from left to right. Store the product of all elements to the left of each index in `answer[i]`.
3. Initialize a variable `suffix = 1`.
4. Traverse the array from right to left. Multiply each `answer[i]` by the product of all elements to its right.
5. Update `suffix` after processing each element.
6. Return the completed `answer` array.

This approach avoids division and correctly handles arrays containing zeros.

## Complexity Analysis

### Time Complexity: O(N)

The algorithm traverses the array twice: once from left to right and once from right to left. Each traversal takes `O(N)` time.

Therefore, the total time complexity is **O(N)**, where `N` is the length of the array.

### Space Complexity: O(1) Auxiliary Space

The algorithm uses only two additional variables, `prefix` and `suffix`, beyond the output array.

Therefore, the auxiliary space complexity is **O(1)**, excluding the output array. The output array itself requires `O(N)` space.

## Key Concepts Learned

- Arrays and iteration
- Prefix products
- Suffix products
- Space optimization
- Avoiding division
- Time and space complexity analysis

## Conclusion

LeetCode 238: Product of Array Except Self can be solved efficiently using prefix and suffix products. The solution achieves `O(N)` time complexity, uses `O(1)` auxiliary space excluding the output array, and handles zero and negative values without using division.
