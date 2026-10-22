# LeetCode 322: Coin Change

## Problem Statement

You are given an integer array `coins` representing different coin denominations and an integer `amount` representing a total amount of money.

Return the **fewest number of coins** needed to make up that amount. If the amount cannot be made up by any combination of the coins, return `-1`.

You may assume that you have an unlimited number of each kind of coin.

### Example 1

**Input:**
```python
coins = [1, 2, 5]
amount = 11
```

**Output:**
```python
3
```

**Explanation:**

The amount 11 can be made using `5 + 5 + 1 = 11`. Therefore, the minimum number of coins required is 3.

### Example 2

**Input:**
```python
coins = [2]
amount = 3
```

**Output:**
```python
-1
```

**Explanation:**

It is impossible to make the amount 3 using only coins of denomination 2.

### Example 3

**Input:**
```python
coins = [1]
amount = 0
```

**Output:**
```python
0
```

**Explanation:**

No coins are needed to make an amount of 0.

---

## Python Solution

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [float('inf')] * (amount + 1)
        dp[0] = 0

        for coin in coins:
            for current_amount in range(coin, amount + 1):
                dp[current_amount] = min(
                    dp[current_amount],
                    dp[current_amount - coin] + 1
                )

        return dp[amount] if dp[amount] != float('inf') else -1
```

---

## Approach: Dynamic Programming

We use **Dynamic Programming (DP)** to find the minimum number of coins needed for every amount from `0` to `amount`.

1. **Initialize the DP array:** Create an array `dp` of size `amount + 1`. Set every value to infinity because initially, we do not know how to make each amount.
2. **Base case:** Set `dp[0] = 0`, because zero coins are needed to make an amount of zero.
3. **Process each coin:** For every coin, check each amount that the coin can help make.
4. **Update the minimum:** Use the formula:

   `dp[current_amount] = min(dp[current_amount], dp[current_amount - coin] + 1)`

   This compares the current best answer with the answer obtained by using one additional coin.
5. **Return the result:** If `dp[amount]` is still infinity, return `-1`. Otherwise, return the minimum number of coins.

### Example Walkthrough

For `coins = [1, 2, 5]` and `amount = 11`:

- Using coin `1`, we can make every amount from 1 to 11.
- Using coin `2`, we can improve the minimum number of coins for several amounts.
- Using coin `5`, we can improve the results further.
- The final value is `dp[11] = 3`, because `5 + 5 + 1 = 11`.

---

## Complexity Analysis

Let:
- `n` = number of coin denominations.
- `A` = the target amount.

### Time Complexity

**O(n × A)**

We process every coin and iterate through amounts from that coin up to the target amount.

### Space Complexity

**O(A)**

The DP array stores the minimum number of coins for each amount from `0` to `A`.

---

## Key Concepts

- Dynamic Programming
- One-dimensional DP
- Array manipulation
- Optimization
- Minimum-value calculations

---

## Conclusion

LeetCode 322, Coin Change, is a classic Dynamic Programming problem. By storing the minimum number of coins needed for smaller amounts, we can efficiently calculate the answer for the target amount.

**Time Complexity:** `O(n × A)`

**Space Complexity:** `O(A)`
