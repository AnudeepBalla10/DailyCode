# Stairmaster

This question is asked by Apple.

>Given a staircase where the ith step has a non-negative cost associated with it given by cost[i], return the minimum cost of climbing to the top of the staircase. You may climb one or two steps at a time and you may start climbing from either the first or second step.

Ex: Given the following cost array…
```
cost = [5, 10, 20], return 10.
```
Ex: Given the following cost array…
```
cost = [1, 5, 10, 3, 7, 2], return 10.
```

LeetCode: https://leetcode.com/problems/min-cost-climbing-stairs/

# Dynamic programming approach
```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int[] dp = new int[cost.length + 1];

        for (int i = 2; i <= cost.length; i++) {
            int oneStep = dp[i - 1] + cost[i - 1];
            int twoStep = dp[i - 2] + cost[i - 2];
            dp[i] = Math.min(oneStep, twoStep);
        }
        return dp[cost.length];
    }
}
