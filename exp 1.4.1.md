# LeetCode 234: Palindrome Linked List

## Problem Statement

Given the head of a singly linked list, return `true` if it is a palindrome or `false` otherwise.

A palindrome is a sequence that reads the same forward and backward.

### Example 1

**Input:**
```text
head = [1,2,2,1]
```

**Output:**
```text
true
```

**Explanation:** The linked list reads `1 → 2 → 2 → 1`, which is the same forward and backward.

### Example 2

**Input:**
```text
head = [1,2]
```

**Output:**
```text
false
```

**Explanation:** The sequence `1 → 2` is not the same when reversed.

## Solution (Python)

```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        values = []
        current = head

        while current:
            values.append(current.val)
            current = current.next

        return values == values[::-1]
```

## Approach

The solution uses an array to store the linked list's values and checks whether the array is a palindrome.

1. Create an empty list named `values`.
2. Traverse the linked list from the head to the end.
3. Append each node's value to `values`.
4. Reverse the array using `values[::-1]`.
5. Compare the original array with the reversed array.
6. Return `true` if both arrays are equal; otherwise, return `false`.

## Complexity Analysis

### Time Complexity: O(N)

The algorithm traverses the linked list once to collect its values and compares the array with its reverse. Both operations take linear time, so the overall time complexity is `O(N)`, where `N` is the number of nodes.

### Space Complexity: O(N)

The algorithm stores all `N` node values in an additional array. Therefore, the auxiliary space complexity is `O(N)`.

## Key Concepts Learned

- Singly linked lists
- Palindromes
- Array traversal
- Array reversal
- Time and space complexity analysis

## Conclusion

LeetCode 234: Palindrome Linked List can be solved by copying linked-list values into an array and comparing the array with its reverse. This straightforward approach takes `O(N)` time and `O(N)` auxiliary space.
