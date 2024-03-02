# Longest Common Subsequence

 👓This question is asked by Google.👓

>Given two strings, s and t, return the length of their longest subsequence.

Ex: Given the following strings s and t…
```
s = "xyz", t = "xyz". return 3.
```
Ex: Given the following strings s and t…
```
s = "abca", t = "acea", return 3.
```
Ex: Given the following strings s and t…
```
s = "abc", t = "def", return 0.
```
## LeetCode: https://leetcode.com/problems/longest-common-subsequence/

## Simple Approach
```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        if (text1.equals(text2)) {
            return text1.length();
        }

        if (text2.length() > text1.length()) {
            return longestCommonSubsequence(text2, text1);
        }

        char[] s1 = text1.toCharArray();
        char[] s2 = text2.toCharArray();

        int[] prev = new int[s2.length + 1];
        int[] curr = new int[s2.length + 1];

        for (int i = 0; i < s1.length; i++) {
            for (int j = 0; j < s2.length; j++) {
                if (s1[i] == s2[j]) {
                    curr[j + 1] = prev[j] + 1;
                } else {
                    curr[j + 1] = Math.max(curr[j], prev[j + 1]);
                }
            }

            var temp = prev;
            prev = curr;
            curr = temp;
        }

        // the original answer is in prev
        return prev[prev.length - 1];
    }
}
