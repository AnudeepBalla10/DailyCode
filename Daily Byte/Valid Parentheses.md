# Valid Parentheses

👓This question is asked by Google.👓

> Given a string only containing the following characters (, ), {, }, [, and ] return whether or not the opening and closing characters are in a valid order.

Ex: Given the following strings...

- "(){}[]", return true
- "(({[]}))", return true
- "{(})", return false

```java
class Solution {
    public boolean isValid(String s) {
       Stack<Character> stack = new Stack<>();

        for (char c : s.toCharArray()) {
            if (c == '(' || c == '{' || c == '[') {
                stack.push(c);
            } else if (!stack.isEmpty() && isMatching(stack.peek(), c)) {
                stack.pop();
            } else {
                return false;
            }
        }

        return stack.isEmpty();
    }
        private boolean isMatching(char left, char right) {
        return (left == '(' && right == ')') ||
               (left == '{' && right == '}') ||
               (left == '[' && right == ']');
    }
  
}
```
