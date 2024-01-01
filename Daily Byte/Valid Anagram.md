# Valid Anagram


📖 This question is asked by Facebook.📖  

> Given two strings s and t return whether or not s is an anagram of t.
Note: An anagram is a word formed by reordering the letters of another word.

Ex: Given the following strings...

- s = "cat", t = "tac", return true
- s = "listen", t = "silent", return true
- s = "program", t = "function", return false


```java
import java.util.Arrays;

class HelloWorld {
    public static void main(String[] args) {
        System.out.println(validAnagram("cat", "tac"));
        System.out.println(validAnagram("listen", "silent"));
        System.out.println(validAnagram("program", "function"));
    }
    
    public static boolean validAnagram(String s, String t){
        if (s.length() != t.length()) {
            return false;
        }
        char[] x = s.toCharArray();
        char[] y = t.toCharArray();
        Arrays.sort(x);
        Arrays.sort(y);
        
        return Arrays.equals(x,y);
    }
}
```
