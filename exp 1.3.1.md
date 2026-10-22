# LeetCode 232: Implement Queue using Stacks

## Problem Statement

Implement a first-in-first-out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue:

- `push(x)`: Pushes element `x` to the back of the queue.
- `pop()`: Removes the element from the front of the queue and returns it.
- `peek()`: Returns the element at the front of the queue.
- `empty()`: Returns `true` if the queue is empty, otherwise returns `false`.

You must use only standard stack operations, such as pushing an element, peeking at the top element, popping from the top, checking the size, and checking whether the stack is empty.

## Example

**Input:**
```text
["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]
```

**Output:**
```text
[null, null, null, 1, 1, false]
```

**Explanation:**

```text
MyQueue myQueue = new MyQueue();
myQueue.push(1);    // Queue: [1]
myQueue.push(2);    // Queue: [1, 2]
myQueue.peek();     // Returns 1
myQueue.pop();      // Returns 1, queue becomes [2]
myQueue.empty();    // Returns false
```

## Solution (Python)

```python
class MyQueue:

    def __init__(self):
        self.input_stack = []
        self.output_stack = []

    def push(self, x: int) -> None:
        self.input_stack.append(x)

    def pop(self) -> int:
        self.peek()
        return self.output_stack.pop()

    def peek(self) -> int:
        if not self.output_stack:
            while self.input_stack:
                self.output_stack.append(self.input_stack.pop())

        return self.output_stack[-1]

    def empty(self) -> bool:
        return not self.input_stack and not self.output_stack
```

## Approach

The solution uses **two stacks** to implement a queue.

1. **Initialize:** Create two empty stacks, `input_stack` and `output_stack`.
2. **Push:** Add new elements to `input_stack`.
3. **Peek:** If `output_stack` is empty, move all elements from `input_stack` to `output_stack`. This reverses their order, placing the oldest element on top. Return the top element of `output_stack`.
4. **Pop:** Call `peek()` to ensure the oldest element is on top, then remove and return it.
5. **Empty:** Return `True` only when both stacks are empty.

The transfer of elements happens only when `output_stack` is empty, allowing the queue to preserve FIFO order efficiently.

## Complexity Analysis

Let `N` represent the number of elements in the queue.

| Operation | Time Complexity |
|---|---|
| `push(x)` | `O(1)` |
| `pop()` | `O(1)` amortized |
| `peek()` | `O(1)` amortized |
| `empty()` | `O(1)` |

### Time Complexity

Each element is pushed onto `input_stack` once, transferred to `output_stack` at most once, and popped from `output_stack` at most once. Therefore, `pop()` and `peek()` take **O(1) amortized time**, although a single call can take `O(N)` when transferring elements.

### Space Complexity: O(N)

The two stacks can collectively store up to `N` elements. Therefore, the auxiliary space complexity is `O(N)`.

## Key Concepts Learned

- Stack and queue data structures
- FIFO and LIFO principles
- Implementing one data structure using another
- Python lists as stacks
- Amortized time complexity

## Conclusion

LeetCode 232 demonstrates how two stacks can implement a FIFO queue. By transferring elements only when the output stack is empty, the solution achieves amortized `O(1)` time for push, pop, and peek operations, with `O(N)` auxiliary space.
