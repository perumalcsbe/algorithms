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
step1: create low and high counter
step2: for every character
        1. increment low if character is '(' open
        2. decrement low if character is not '(' open in other words ')' close or '*'
        1. increment high if character is not ')' close in other words '(' open or '*'
        2. decrement high if character is ')' or '*' close
        if high below 0 then unbalanced
        take max of low
step3: return true if low is 0

e.g. "()"
step1: low = 0, high = 0
step2: "()"
       low = 1
       high = 1
               low = 0
               high = 0              
 e.g. "(***)"
         low = 0, high = 0
         low = 1
         high = 1
                 low = 0
                 high = 2
                         low = 0 // -1
                         high = 3
                                 
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



