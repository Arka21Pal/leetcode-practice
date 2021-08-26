# Coin Change, a classic problem.

Often used to show how "dp" (dynamic programming) works. The premise is simple, calculate the least number of coins to add up to a certain amount. Needless to say, I couldn't solve it myself (being a beginner at dp).

Link: https://leetcode.com/problems/coin-change/

## My solution:

```python

# If we consider every index as its own problem, then it's obvious that we can build on a previous problem for the current problem.
# Say, for an amount of 1, we would need only one "1" coin. For an amount of 2, we would need one coin of "2".
# But for an amount of 3, we would need a coin of "2" and a coin of "1", which makes it 2 coins. dp[i-coin[j]] would be the value of dp[2], in this case, which is 1. But we add 1 to the value of dp (because we assume that we've already taken the coin). This is why it works.
# Admittedly, this was almost impossible for me to think about, and I'm still kind of unclear on "why" it works. But for now, I've understood the problem, so that's good.

class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        
        # Reduces run time.
        coins.sort()
        
        # The basic starting point of the algorithm.
        # This signifies that every element till the index of "amount+1" is it's own problem (first video).
        # So, we start by solving the smaller problems (dp[1], dp[2] etc), before using those to springboard to our solution for the "real" problem, that is dp[amount].

        dp = [float("inf") for i in range(amount+1)]
        dp[0] = 0
        
        # The for loop to check the amount and coins against each other.
        for i in range(amount+1):
            for j in range(len(coins)):
                if coins[j] <= i: # Obviously, you wouldn't want to take coins that are bigger than the amount.
                    
                    # The big part. Here, we're checking for a minimum of the previously filled float("inf"), or the new dp[i-coins[j]].
                    dp[i] = min(dp[i], dp[i - coins[j]] + 1)

                else:
                    break
        if dp[amount] > amount: return -1
        else: return dp[amount]
```

## Resources:

The reason I'm putting these before the solutions, is because the solutions are nothing special in themselves. It's these 2 videos that actually helped me in understanding why we're making the `dp` array, and why we're typing `dp[i] = min(dp[i], dp[i - coins[j]] + 1)` in the `for` loop.

- [AMAZON CODING INTERVIEW QUESTION - COIN CHANGE (LeetCode)](https://www.youtube.com/watch?v=1R0_7HqNaW0)
    - This guy explains really well. At `07:15` he mentions that the he hopes (we hope) that we have already solved the previous problem, thus we can now use the values of the previous elements of the `dp` array (highlighted step above). This explanation makes more sense by watching the next video.
- [Coin Change | Live Coding with Explanation | Leetcode - 322](https://www.youtube.com/watch?v=hxaTNNQmx4c)
    - Here, she shows (visually) how the `min` part in the loop is working. The values from the previous elements in the array fit in nicely to give the most optimal solution to the problem.
    - As the guy in the previous video mentioned, we are assuming that we have already solved a smaller problem already, and so we can hopefully use the values of the previous elements in our `dp` array. She shows this visually, and we see how nicely the lowest number of coins needed for one number (element of `dp` array) slots in to produce the minimum number of coins to produce the next "amount".

This is very rudimentary explanation, so probably won't make any sense now. I will attempt to write some more comments in the code too, just in case. Anyway, just watch the videos.

## Some other solutions, essentially same concept:

- Link: https://leetcode.com/problems/coin-change/discuss/1023069/Python-or-DP

(This one is so short, makes it look even more elegant)

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [0]+[float("inf")]*amount
        for val in range(min(coins),amount+1):
            dp[val] = min([dp[val-coin] for coin in coins if coin<=val]+[float("inf")])+1
            
        return dp[-1] if not dp[-1] == float("inf") else -1
```

- Link: https://leetcode.com/problems/coin-change/discuss/1376318/Python-3-Tabulation-(Bottom-Up)-aatalyk

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [float("inf") for i in range(amount+1)]
        dp[0] = 0  # Base case when amount is 0 then coins needed is also 0
        for i in range(1, amount+1):
            for j in range(len(coins)):
                if (coins[j] <= i):
                    dp[i] = min(dp[i], dp[i - coins[j]] + 1)
        
        print(dp)
        return -1 if dp[-1] == float("inf") else dp[-1]
```
