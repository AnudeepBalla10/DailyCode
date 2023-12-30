# Valid Palindrome with Remova


📖 This question is asked by Facebook.📖


> Given a string and the ability to delete at most one character, return whether or not it can form a palindrome.
Note: a palindrome is a sequence of characters that reads the same forwards and backwards.

Ex: Given the following strings...

##### "abcba", return true
##### "foobof", return true (remove the first 'o', the second 'o', or 'b')
##### "abccab", return false

```java

public class Solution {
    public static boolean validPalindrome(String s) {
        int left = 0;
        int right = s.length() - 1;

        while (left < right) {
            if (s.charAt(left) != s.charAt(right)) {
                // Check if skipping the character at the left pointer forms a palindrome
                if (isPalindrome(s, left + 1, right)) {
                    return true;
                }
                // Check if skipping the character at the right pointer forms a palindrome
                if (isPalindrome(s, left, right - 1)) {
                    return true;
                }
                // If neither option results in a palindrome, return false
                return false;
            }
            left++;
            right--;
        }

        // The string is already a palindrome or can be made one by deleting at most one character
        return true;
    }

    private static boolean isPalindrome(String s, int start, int end) {
        while (start < end) {
            if (s.charAt(start) != s.charAt(end)) {
                return false;
            }
            start++;
            end--;
        }
        return true;
    }

    public static void main(String[] args) {
        System.out.println(validPalindrome("aba"));  // Output: true
        System.out.println(validPalindrome("aacbaa")); // Output: true
        System.out.println(validPalindrome("abc"));  // Output: false
    }
}

```
