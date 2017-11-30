Implement an algorithm to determine if a string has all unique characters.

**Example**

Given`"abc"`, return`true`.

Given`"aab"`, return`false`.

[**Challenge**](http://www.lintcode.com/en/problem/unique-characters/#challenge)

What if you can not use additional data structures?



```java
public class Solution {
    /*
     * @param str: A string
     * @return: a boolean
     */
    public boolean isUnique(String str) {
        Set<Character> set = new HashSet<>();
        
        for (int i = 0; i < str.length(); i++) {
            char ch = str.charAt(i);
            if (set.contains(ch)) {
                return false;
            }
            
            set.add(ch);
        }
        
        return true;
    }
}
```



