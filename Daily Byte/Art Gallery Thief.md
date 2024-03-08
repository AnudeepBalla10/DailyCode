# Art Gallery Thief

> You’ve broken into an art gallery and want to maximize the value of the paintings you steal. All the paintings you steal you place in your bag which can hold at most W pounds. Given that the weight and value of the ith painting is given by weights[i] and values[i] respectively, return the maximum value you can steal.

Ex: Given the following W, weights array and values array…
```
W = 10, weights = [4, 1, 3], values = [4, 2, 7], return 13.
```

## Dynamic Programming Approach && Knapsack

```java
public class Knapsack {
    public static int maxStealValue(int W, int[] weights, int[] values) {
        int n = weights.length;
        int[][] dp = new int[n + 1][W + 1];

        for (int i = 1; i <= n; i++) {
            for (int w = 1; w <= W; w++) {
                if (weights[i - 1] <= w) {
                    dp[i][w] = Math.max(dp[i - 1][w], values[i - 1] + dp[i - 1][w - weights[i - 1]]);
                } else {
                    dp[i][w] = dp[i - 1][w];
                }
            }
        }

        return dp[n][W];
    }

    public static void main(String[] args) {
        int W = 10;
        int[] weights = {4, 1, 3};
        int[] values = {4, 2, 7};
        System.out.println("Maximum value that can be stolen: " + maxStealValue(W, weights, values));
    }
}
