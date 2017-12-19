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

**Approach: Two Pointers**

```
i = 0, j=0
s = "aab" 
p = "c*a*b"

case1: false { s[i] == p[j]

p = "?a*b"
s = "aab" 
i=0,j=0;match=0;star=0  : advance pointers { p[0] == '?' 
i=1,j=1                 : advance pointers { s[1] == p[1]
i=2;j=2                 : advance pattern { p[2] == '*'
i=2;match=2,star=2;j=3  : advance string { star != -1
i=3;match=3,star=2;j=4

true { j == p.length()
```

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



