Given a string, find the length of the longest substring without repeating characters.

**Example**

For example, the longest substring without repeating letters for`"abcabcbb"`is`"abc"`, which the length is`3`.

For`"bbbbb"`the longest substring is`"b"`, with the length of`1`.

[**Challenge**](http://lintcode.com/en/problem/longest-substring-without-repeating-characters/#challenge)

O\(n\) time

```
a b c a b c b b
1 1 1 0 1 2 1 1
a b c d e f g h i j k l m n o p q r s t u v w x y z
1 1 1
2
b b b b b
1 1 1 1 1
```

```java
public class Solution {
    /*
     * @param s: a string
     * @return: an integer
     */
    public int lengthOfLongestSubstring(String s) {
        int max = 0;
        int i = 0;
        int j = 0;
        boolean[] exists = new boolean[256];
        
        while (j < s.length()) {
            // reset for dup
            while (exists[s.charAt(j)]) {
                exists[s.charAt(i)] = false;
                i++;
            }
            exists[s.charAt(j)] = true;
            max = Math.max(max, j - i+1);
            
            j++;
            
        }
        
        
        return max;
    }
}
```



