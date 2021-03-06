Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

##### Notice

Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.

**Example**

`"A man, a plan, a canal: Panama"`is a palindrome.

`"race a car"`is not a palindrome.

O\(n\) time without extra memory.

[http://www.lintcode.com/en/problem/valid-palindrome/](http://www.lintcode.com/en/problem/valid-palindrome/)

**Approach: Two Pointers**

```
1. base case: true { if s is empty
2. Traverse String from both ends, left & right pointer
     case1. left++ { if char is not an alphabet
     case2. right++ { if char is not an alphabet
     case3. left++ & right++ { if there is a match between left & right characters
     case4. false { if no match in left & right end characters
3. true { if above traverse complete
```

```java
    /*
     * @param s: A string
     * @return: Whether the string is a valid palindrome
     */
    public boolean isPalindrome(String s) {
        if (s.length() == 0) {
            return true;
        }

        int l = 0;
        int r = s.length() - 1;

        while (l < r) {
            char cl = s.charAt(l);
            char cr = s.charAt(r);
            if (!Character.isLetter(cl) && !Character.isDigit(cl)) {
                l++;
            } else  if (!Character.isLetter(cr) && !Character.isDigit(cr)) {
                r--;
            } else if (Character.toLowerCase(cl) == Character.toLowerCase(cr)) {
                l++;
                r--;
            } else {
                return false;
            }

        }

        return true;
    }
```

```java
public class Solution {
    public int isPalindrome(String A) {
        int start = 0;
        int end = A.length() - 1;
        A = A.toLowerCase();
        while (start < end) {
            while(start < end && !Character.isLetter(A.charAt(start)) && !Character.isDigit(A.charAt(start))) {
                start++;
            }
            
            while(start < end && !Character.isLetter(A.charAt(end)) && !Character.isDigit(A.charAt(end))) {
                end--;
            }
            
            if (A.charAt(start) != A.charAt(end)) {
                return 0;
            } 
            
            start++;
            end--;
            
        }
        
        return 1;
        
    }
}

```



