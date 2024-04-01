# Is Monotonic
📖This question is asked by Facebook.📖

> Given an array nums, return whether or not its values are monotonically increasing or monotonically decreasing.


Ex: Given the following array nums…
```
nums = [1, 2, 3, 4, 4, 5], return true.
```
Ex: Given the following array nums…
```
nums = [7, 6, 3], return true.
```
Ex: Given the following array nums…
```
nums = [8, 4, 6], return false.
```
Note: An array is monotonically increasing if for all values i <= j, nums[i] <= nums[j].
Similarly an array is monotonically decreasing if for all values i <= j, nums[i] >= nums[j].


```
class Solution {
    public boolean isMonotonic(int[] nums) {
        if (nums.length <= 1) {
            return true;
        }
        
        // Determine the monotonicity direction or if it's undecided yet
        boolean increasing = false;
        boolean decreasing = false;
        
        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] < nums[i + 1]) {
                increasing = true;
            } else if (nums[i] > nums[i + 1]) {
                decreasing = true;
            }
            
            // If both increasing and decreasing flags are true, the array is not monotonic
            if (increasing && decreasing) {
                return false;
            }
        }
        
        // If the loop completes without finding contradictory evidence, the array is monotonic
        return true;
    }
}
