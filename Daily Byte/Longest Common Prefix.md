# Longest Common Prefix

🤠This question is asked by Microsoft. 🤠

> Given an array of strings, return the longest common prefix that is shared amongst all strings.

Note: you may assume all strings only contain lowercase alphabetical characters.

Ex: Given the following arrays...

- ["colorado", "color", "cold"], return "col"

- ["a", "b", "c"], return ""

- ["spot", "spotty", "spotted"], return "spot"

```java
public class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0)
            return "";

        String prefix = strs[0];
        for (String str : strs) {
            while (str.indexOf(prefix) != 0) {
                prefix = prefix.substring(0, prefix.length() - 1);
            }

        }
        return prefix;
    }
}
```
