Implement wildcard pattern matching with support for`'?'`and`'*'`.

```
'?' Matches any single character.
'*' Matches any sequence of characters (including the empty sequence).

The matching should cover the 
entire
 input string (not partial).

The function prototype should be:
bool isMatch(const char *s, const char *p)

Some examples:
isMatch("aa","a") → false
isMatch("aa","aa") → true
isMatch("aaa","aa") → false
isMatch("aa", "*") → true
isMatch("aa", "a*") → true
isMatch("ab", "?*") → true
isMatch("aab", "c*a*b") → false
```

**Approach: **

```java
class Solution {
    public boolean isMatch(String s, String p) {
        int i = 0, j = 0, match = 0, star = -1;
        
        while (i < s.length()) {
            if (j < p.length() && (s.charAt(i) == p.charAt(j) || p.charAt(j) == '?')) {
                i++;
                j++;
            } else if (j < p.length() && p.charAt(j) == '*') {
                star = j;
                match = i;
                j++;
            } else if (star != -1) {
                j = star + 1;
                match++;
                i = match;
            } else {
                return false;
            }
        }
        
        while (j < p.length() && p.charAt(j) == '*') {
            j++;
        }
        
        return j == p.length();
    }
}     
      
```



