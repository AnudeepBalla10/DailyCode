# Compare Keystrokes

🌴This question is asked by Amazon.🌴

> Given two strings s and t, which represents a sequence of keystrokes, where # denotes a backspace, return whether or not the sequences produce the same result.

Ex: Given the following strings...

- s = "ABC#", t = "CD##AB", return true
- s = "como#pur#ter", t = "computer", return true
- s = "cof#dim#ng", t = "code", return false

  LeetCode: https://leetcode.com/problems/backspace-string-compare

  ## Appraoch
  Use `Stack`, if `#` is found pop the last char.


   ```java
   
   class Solution {
    public boolean backspaceCompare(String s, String t) {
      return buildString(s).equals(buildString(t));
    }

    String buildString(String str) {
        Stack<Character> stack = new Stack<>();

        for (char ch : str.toCharArray()) {
            if (ch == '#') {
                if (!stack.isEmpty()) {
                    stack.pop(); // Backspace: Remove the previous character
                }
            } else {
                stack.push(ch);
            }
        }

        // Build the final string
        StringBuilder result = new StringBuilder();
        while (!stack.isEmpty()) {
            result.insert(0, stack.pop());
        }

        return result.toString();
    }
    }

```
