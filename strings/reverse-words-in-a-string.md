Given an input string, reverse the string word by word.

For example,  
Given s = "`the sky is blue`",  
return "`blue is sky the`".

**Clarification**

* What constitutes a word?
  A sequence of non-space characters constitutes a word.
* Could the input string contain leading or trailing spaces?
  Yes. However, your reversed string should not contain leading or trailing spaces.
* How about multiple spaces between two words?
  Reduce them to a single space in the reversed string.

```java
public class Solution {
    /*
     * @param s: A string
     * @return: A string
     */
    public String reverseWords(String s) {
        if (s == null || s.length() == 0) return s;
        
        StringBuilder sb = new StringBuilder();
        String[] arr = s.split(" ");
        String[] res = new String[arr.length];
        for(int i = arr.length - 1; i >= 0; i--) {
            if (arr[i].trim().length() > 0) {
                sb.append(arr[i]);
                if (i > 0) {
                    sb.append(" ");
                }
            }
        }
        
        
        return sb.toString();
    }
}
```



