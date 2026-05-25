# LeetCode 20 - Valid Parentheses

## Problem Statement
Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

A string is valid if:
- Open brackets are closed by the same type of brackets.
- Open brackets are closed in the correct order.
- Every closing bracket has a corresponding opening bracket.

---

## Examples

### Example 1
Input:
```text
s = "()"
```

Output:
```text
true
```

### Example 2
Input:
```text
s = "()[]{}"
```

Output:
```text
true
```

### Example 3
Input:
```text
s = "(]"
```

Output:
```text
false
```

---

## Approach
We use a **Stack** data structure.

### Steps
1. Traverse each character in the string.
2. If the character is an opening bracket (`(`, `{`, `[`), push it onto the stack.
3. If the character is a closing bracket:
   - Check if the stack is empty.
   - Pop the top element and verify it matches the correct opening bracket.
4. After processing all characters:
   - If the stack is empty → valid.
   - Otherwise → invalid.

---

## Java Solution

```java
import java.util.*;

class Solution {
    public boolean isValid(String s) {

        Stack<Character> stack = new Stack<>();

        for (char ch : s.toCharArray()) {

            if (ch == '(' || ch == '{' || ch == '[') {
                stack.push(ch);
            } 
            else {

                if (stack.isEmpty()) {
                    return false;
                }

                char top = stack.pop();

                if ((ch == ')' && top != '(') ||
                    (ch == '}' && top != '{') ||
                    (ch == ']' && top != '[')) {
                    return false;
                }
            }
        }

        return stack.isEmpty();
    }
}
```

---

## Complexity Analysis

- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(n)`

Where `n` is the length of the string.

---

## Key Concept
A **stack** follows **LIFO (Last In First Out)**, which perfectly matches the bracket closing order requirement.
