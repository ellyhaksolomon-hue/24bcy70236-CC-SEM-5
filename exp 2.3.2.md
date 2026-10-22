# LeetCode 287: Find the Duplicate Number

## Problem Statement

Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive.

There is only one repeated number in `nums`, but it may appear more than once. Return this repeated number.

You must solve the problem without modifying the array and using only constant extra space.

### Example 1

**Input:**
```text
nums = [1,3,4,2,2]
```

**Output:**
```text
2
```

**Explanation:** The number `2` appears more than once in the array.

### Example 2

**Input:**
```text
nums = [3,1,3,4,2]
```

**Output:**
```text
3
```

**Explanation:** The number `3` is repeated in the array.

### Example 3

**Input:**
```text
nums = [3,3,3,3,3]
```

**Output:**
```text
3
```

**Explanation:** Every element is `3`, so the repeated number is `3`.

## Solution (Python)

```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        slow = nums[0]
        fast = nums[0]

        # Find the intersection point
        while True:
            slow = nums[slow]
            fast = nums[nums[fast]]

            if slow == fast:
                break

        # Find the entrance to the cycle
        slow = nums[0]

        while slow != fast:
            slow = nums[slow]
            fast = nums[fast]

        return slow
```

## Approach

The solution uses **Floyd's Tortoise and Hare Algorithm**, also known as the cycle detection algorithm.

### Step 1: Detect the cycle

- Initialize two pointers, `slow` and `fast`, at the first element.
- Move `slow` one step at a time.
- Move `fast` two steps at a time.
- Continue until both pointers meet.

### Step 2: Find the duplicate

- Reset `slow` to the first element.
- Keep `fast` at the meeting point.
- Move both pointers one step at a time.
- When they meet again, their meeting value is the duplicate number.

### Why does it work?

Treat each array value as the index of the next element. Because the array contains a duplicate, this sequence forms a cycle. Floyd's algorithm identifies the cycle's entrance, which corresponds to the duplicate number.

## Complexity Analysis

### Time Complexity: O(N)

Both pointer traversals take linear time in the worst case, where `N` is the length of the array.

Therefore, the overall time complexity is **O(N)**.

### Space Complexity: O(1)

The algorithm uses only two pointers, `slow` and `fast`, and does not create additional data structures or modify the input array.

Therefore, the auxiliary space complexity is **O(1)**.

## Key Concepts Learned

- Arrays
- Two-pointer technique
- Floyd's cycle detection algorithm
- Linked-list cycle concepts
- Constant-space algorithms
- Time and space complexity analysis

## Conclusion

LeetCode 287: Find the Duplicate Number can be solved efficiently using Floyd's Tortoise and Hare Algorithm. This approach finds the duplicate in `O(N)` time and `O(1)` auxiliary space without modifying the original array.
