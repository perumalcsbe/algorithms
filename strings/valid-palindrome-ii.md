Given a non-empty string`s`, you may delete **at most **one character. Judge whether you can make it a palindrome.

**Example 1:**

```
Input:"aba"
Output:True
```

**Example 2:**

```
Input:"abca"
Output:True
Explanation: You could delete the character 'c'.
```

**Note:**

1. The string will only contain lowercase characters a-z. The maximum length of the string is 50000.

**Approach: Recursive**

1. Traverse string from start and end if no match then either left or right \(include  or exclude\)
2. recursively check if any one of them solves

```java
class Solution {
    public boolean validPalindrome(String s) {
        
        int l = -1;
        int r = s.length();
        
        while (++l < --r) {
            if (s.charAt(l) != s.charAt(r)) {
                return validPalindrome(s, l, r+1) || validPalindrome(s, l-1, r);
            }
        }
        
        return true;
    }
    
    private boolean validPalindrome(String s, int l, int r) {
        while (++l < --r) {
            if (s.charAt(l) != s.charAt(r)) {
                return false;
            }
        }
        
        return true;
    }
}
```



