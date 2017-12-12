Given a string containing only three types of characters: '\(', '\)' and '\*', write a function to check whether this string is valid. We define the validity of a string by these rules:

1. Any left parenthesis`'('`must have a corresponding right parenthesis`')'`.
2. Any right parenthesis`')'`must have a corresponding left parenthesis`'('`.
3. Left parenthesis`'('`must go before the corresponding right parenthesis`')'`.
4. `'*'`could be treated as a single right parenthesis`')'`or a single left parenthesis`'('`or an empty string.
5. An empty string is also valid.

**Example 1:**

```
Input:"()"
Output: True
```

**Example 2:**

```
Input: "(*)"
Output: True
```

**Example 3:**

```
Input: "(*))"
Output: True
```

**Approach: BackTracking**

```
step1: base case
      return true if string is empty or string == '*'
Step2: count open parenthesis 
        1. excluding *
        2. including *
Step3: Recursively call method to remove corresponding close parenthesis
        1. excluding * if not included 
        2. including * if excluded               
```

```java
class Solution {
    public boolean checkValidString(String s) {
        int lo = 0;
        int hi = 0;
        for (char ch: s.toCharArray()) {
            lo += ch == '(' ? 1 : -1;
            hi += ch != ')' ? 1 : -1;
            
            if (hi < 0) {
                break;
            }
            lo = Math.max(lo, 0);
        }
        
        return lo == 0;
    }
}
```



