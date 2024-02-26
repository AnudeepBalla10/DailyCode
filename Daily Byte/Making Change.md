# Making Change

📖This question is asked by Facebook.📖
 
 > Given an array that represents different coin denominations and an amount of change you need to make, return the fewest number of coins it takes to make the given amount of change.
Note: If it is not possible to create the amount of change with the coins you’re given, return -1.

Ex: Given the following denominations and amount…
```
coins = [1,5, 10, 25], amount = 78, return 6
Take three 25 coins and three 1 coins for a total of 6 coins.
```

## Dynamic programming - Bottom up Approach

```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1);
        dp[0] = 0;
        for (int i = 0; i <= amount; i++) {
            for (int coin : coins) {
                if (i - coin < 0) continue;

                dp[i] = Math.min(dp[i], dp[i-coin]+1);

            }
        }
        return dp[amount] == (amount+1) ? -1: dp[amount];
    }
}
