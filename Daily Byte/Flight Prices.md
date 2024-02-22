# Flight Prices

👓This question is asked by Google. 👓

>A company is booking flights to send its employees to its two satellite offices A and B. The cost of sending the ith employee to office A and office B is given by prices[i][0] and prices[i][1] respectively. Given that half the employees must be sent to office A and half the employees must be sent to office B, return the minimum cost the company must pay for all their employees’ flights.

Ex: Give the following prices…
```
prices = [[40,30],[300,200],[50,50],[30,60]], return 310
Fly the first personn to office B.
Fly the second person to office B.
Fly the third person to office A.
Fly the fourth person to office A.
```
# Greedy approach
```java
class Solution {
    public int twoCitySchedCost(int[][] costs) {
        int n = costs.length, totalCost =0;
        Arrays.sort(costs, (a, b) -> (a[0] - a[1]) - (b[0] - b[1]));
        for (int i = 0; i < n / 2; i++) {
            totalCost += costs[i][0] + costs[n - i - 1][1];
        }
        return totalCost;
    }
}
```
