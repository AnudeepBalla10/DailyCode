#Who Wins

🌴This question is asked by Amazon.🌴 

>Given an integer array, two players take turns picking the largest number from the ends of the array. First, player one picks a number (either the left end or right end of the array) followed by player two. Each time a player picks a particular numbers, it is no longer available to the other player. This picking continues until all numbers in the array have been chosen. Once all numbers have been picked, the player with the larger score wins. Return whether or not player one will win.
Note: You may assume that each player is playing to win (i.e. both players will always choose the maximum of the two numbers each turn) and that there will always be a winner.



Ex: Given the following integer array...

```
nums = [1, 2, 3], return true
Player one takes 3
Player two takes 2
Player one takes 1
3 + 1 > 2 and therefore player one wins
```

## Dynamic Programming Approach
```java
class Solution {
    public boolean predictTheWinner(int[] nums) {
        int n = nums.length;
        int[][] dp = new int[n][n];

        //base case when we have only 1 player;
        for(int i =0;i<n;i++){
            dp[i][i] = nums[i];
        }

        for(int len = 1; len < n; len++){
            for(int start=0; start < n-len; start++){
                int end = start + len ;
                dp[start][end] = Math.max(nums[start] - dp[start + 1][end], nums[end] - dp[start][end - 1]);
            }
        }
         // If the score difference is non-negative, player one wins
        return dp[0][n - 1] >= 0;
    }
}
```
