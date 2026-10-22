# LeetCode 84: Largest Rectangle in Histogram

## Problem Statement

Given an array of integers `heights` representing the heights of bars in a histogram, where the width of each bar is `1`, return the area of the largest rectangle that can be formed within the histogram.

### Example 1

**Input:**
```text
heights = [2,1,5,6,2,3]
```

**Output:**
```text
10
```

**Explanation:** The largest rectangle is formed by the bars with heights `5` and `6`. The rectangle has a height of `5` and a width of `2`, giving an area of `5 × 2 = 10`.

### Example 2

**Input:**
```text
heights = [2,4]
```

**Output:**
```text
8
```

**Explanation:** Both bars can form a rectangle of height `2` and width `2`, with an area of `2 × 2 = 4`. The largest rectangle is the second bar alone, with height `4` and width `1`, so the correct output is `4`.

## Solution (Python)

```python
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        stack = []
        max_area = 0

        for i, height in enumerate(heights):
            start = i

            while stack and stack[-1][1] > height:
                index, h = stack.pop()
                max_area = max(max_area, h * (i - index))
                start = index

            stack.append((start, height))

        for index, height in stack:
            max_area = max(max_area, height * (len(heights) - index))

        return max_area
```

## Approach

The solution uses a **monotonic increasing stack** to calculate the largest rectangle efficiently.

1. Initialize an empty stack and set `max_area` to `0`.
2. Traverse the histogram from left to right.
3. Store each bar's starting index and height in the stack.
4. When the current bar is shorter than the bar at the top of the stack, pop the taller bar.
5. Calculate the popped bar's rectangle area using its height and the width between its starting index and the current index.
6. Update `max_area` whenever a larger rectangle is found.
7. After processing all bars, calculate the areas of the remaining bars, extending them to the end of the histogram.
8. Return `max_area`.

The stack maintains bars in increasing height order, allowing the algorithm to determine the maximum rectangle efficiently.

## Complexity Analysis

### Time Complexity: O(N)

Each bar is pushed onto the stack once and popped at most once. Therefore, the total time complexity is `O(N)`, where `N` is the number of bars.

### Space Complexity: O(N)

In the worst case, the stack can contain all `N` bars. Therefore, the auxiliary space complexity is `O(N)`.

## Key Concepts Learned

- Stack data structure
- Monotonic stacks
- Histogram area calculation
- Index tracking
- Optimization from brute force to linear time
- Time and space complexity analysis

## Conclusion

LeetCode 84: Largest Rectangle in Histogram can be solved using a monotonic increasing stack. The algorithm efficiently finds the largest rectangular area in `O(N)` time with `O(N)` auxiliary space.
