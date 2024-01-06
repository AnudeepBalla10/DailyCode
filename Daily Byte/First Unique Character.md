# First Unique Character

 🤠This question is asked by Microsoft.🤠

>Given a string, return the index of its first unique character. If a unique character does not exist, return -1.

Ex: Given the following strings...

- "abcabd", return 2
- "thedailybyte", return 1
- "developer", return 0

### LeetCode: https://leetcode.com/problems/first-unique-character-in-a-string

```java
import java.util.HashMap;
import java.util.Map;
class HelloWorld {
    public static int firstUniqueCharIndex(String s) {
        Map<Character, Integer> charCount = new HashMap<>();

        // Count occurrences of each character
        for (char c : s.toCharArray()) {
            charCount.put(c, charCount.getOrDefault(c, 0) + 1);
        }

        // Find the index of the first unique character
        for (int i = 0; i < s.length(); i++) {
            if (charCount.get(s.charAt(i)) == 1) {
                return i;
            }
        }

        // If no unique character is found, return -1
        return -1;
    }
     public static void main(String[] args) {
        System.out.println(firstUniqueCharIndex("abcabd"));
        System.out.println(firstUniqueCharIndex("thedailybyte"));
        System.out.println(firstUniqueCharIndex("developer"));
        
    }
    
}
```
