Given a string containing just the characters`'('`and`')'`, find the length of the longest valid \(well-formed\) parentheses substring.

For`"(()"`, the longest valid parentheses substring is`"()"`, which has length = 2.

Another example is`")()())"`, where the longest valid parentheses substring is`"()()"`, which has length = 4.

**Analysis**

```
"(" => 0
")" => 0
"()" => 2
"(()" => 2 open: 2 close: 1 => 1+1
")()())" => 4 open 2 close 4 => 2+2

[0, 1, 2, 3, 4, 5]
[), (, ), (, ), )] 
[0, 1, 2, 3, 4, 4]

[0, 1, 2, 3, 4, 5]
[(, (, ), (, ), )] 
[1, 2, 3, 4, 5, 6]

[0, 1, 2, 3, 4, 5]
[(, (, ), (, ), (]
[1, 2, 3, 4, 5, 6]




```

**Approach: DP**



**Approach: Stack**

```java
class Solution {
    public int longestValidParentheses(String s) {
        Stack<Integer> open = new Stack<Integer>();
        int start = -1;
        int max = 0;
        
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(') {
                open.push(i);
            } else {
                // case 1: if stack is empty then invalid close parenthesis found
                if (open.isEmpty()) {
                    start = i; // start new position
                } else {
                    // case 2: if stack is not empty then valid close parenthesis found
                   open.pop();
                    
                    if (open.isEmpty()) {
                        max = Math.max(max, i-start);
                    } else {
                        max = Math.max(max, i-open.peek());
                    }
                }
            }
        }
        
        return max;
    }
}
```

**Approach: Counter**



