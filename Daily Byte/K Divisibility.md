# K Divisibility

> Given an integer array, nums, and a value, k, return the total number of contiguous subarrays that are divisible by k.

Ex: Given the following nums and k…
```
nums = [1, 3, 1, 2, 5], k = 7, return 2 ([1, 3, 1, 2] and [2, 5] both sum to 7).
```

## Prefix sum approach with a hash map

```java

import java.util.HashMap;

public class SubarrayDivisibleByK {
    public static int countSubarraysDivisibleByK(int[] nums, int k) {
        HashMap<Integer, Integer> remainderCount = new HashMap<>();
        remainderCount.put(0, 1); // Base case: a subarray that starts from the beginning

        int prefixSum = 0, count = 0;
        for (int num : nums) {
            prefixSum += num;

            // Calculate remainder and normalize it to be non-negative
            int remainder = prefixSum % k;
            if (remainder < 0) {
                remainder += k;
            }

            // If this remainder has been seen before, add its count to the result
            count += remainderCount.getOrDefault(remainder, 0);

            // Update the frequency of the current remainder
            remainderCount.put(remainder, remainderCount.getOrDefault(remainder, 0) + 1);
        }

        return count;
    }

    public static void main(String[] args) {
        int[] nums = {1, 3, 1, 2, 5};
        int k = 7;
        System.out.println("Result: " + countSubarraysDivisibleByK(nums, k)); // Output: 2
    }
}

```
