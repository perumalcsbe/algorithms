Given a string**s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s **is 1000.

**Example:**

```
Input:"babad"
Output:"bab"
Note:"aba" is also a valid answer.
```

**Example:**

```
Input:"cbbd"
Output:"bb"
```

```
b a b a d
[b] √
[b a] x
[b a b] √
[b a b a] x
[b a b a d] x 
  [a] √
  [a b] x
  [a b a] √
  [a b a d] x
    [b] √
    [b a] x
    [b a d] x

 c b b d
[c] √
[c b] x
[c b b] x
[c b b d] x
  [b] √
  [b b] √
  [b b d] x
     [b] √
     [b d] x
       [d] √
```

```java
class Solution {
    public String longestPalindrome(String s) {
        if (s.length() < 2 || isPalindrome(s)) {
            return s;
        }
        String res = Character.toString(s.charAt(0));
        int maxLen = 0;
        for (int i = 0; i < s.length(); i++) {
            StringBuffer temp = new StringBuffer();
            temp.append(s.charAt(i));
            for (int j = i+1; j < s.length(); j++) {
                temp.append(s.charAt(j));
                if (isPalindrome(temp.toString()) && temp.length() > maxLen) {
                    res = temp.toString();
                    maxLen = temp.length();
                } 
            } 
        }
        
        return res;
    }
    
    private boolean isPalindrome(String p) {
        String reverse = new StringBuffer(p).reverse().toString();
        return p.equals(reverse);
    }
    
}
```



