# Galton Board

👓This question is asked by Google.👓

> A ball is dropped into a special Galton board where at each level in the board the ball can only move right or down. Given that the Galton board has M rows and N columns, return the total number of unique ways the ball can arrive at the bottom right cell of the Galton board.

Ex: Given the following values of M and N…
```
M = 2, N = 2, return 2.
The possible paths are DOWN -> RIGHT and RIGHT -> DOWN
```
Ex: Given the following values of M and N…
```
M = 4, N = 3, return 10.
```

## Dynamic Programming Approach

```java
public class GaltonBoard {
    public static int uniquePaths(int m, int n) {
        int[][] dp = new int[m][n];

        // Fill the dp array
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (i == 0 || j == 0) {
                    dp[i][j] = 1; // Initialize the first row and first column to 1
                } else {
                    dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
                }
            }
        }

        // The bottom right cell contains the total number of unique paths
        return dp[m - 1][n - 1];
    }

    public static void main(String[] args) {
        int m = 2; // Number of rows
        int n = 2; // Number of columns
        System.out.println("Total number of unique paths: " + uniquePaths(m, n));
    }
}

