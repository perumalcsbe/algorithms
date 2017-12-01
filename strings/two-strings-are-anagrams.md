Write a method`anagram(s,t)`to decide if two strings are anagrams or not.

**Clarification**

What is**Anagram**?

* Two strings are anagram if they can be the same after change the order of characters.

**Example**

Given s =`"abcd"`, t =`"dcab"`, return`true`.  
Given s =`"ab"`, t =`"ab"`, return`true`.  
Given s =`"ab"`, t =`"ac"`, return`false`.

[**Challenge**](http://www.lintcode.com/en/problem/two-strings-are-anagrams/#challenge)

O\(n\) time, O\(1\) extra space

```java
public class Solution {
    /**
     * @param s: The first string
     * @param b: The second string
     * @return true or false
     */
    public boolean anagram(String s, String t) {
        if (s.length() != t.length()) return false;

        Map<Character, Integer> map = new HashMap<>();

        for(Character ch : s.toCharArray()) {
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }

        for(Character ch : t.toCharArray()) {
            if (map.containsKey(ch)) {
                int c = map.get(ch);
                if (c > 1) {
                    map.put(ch, c - 1);
                } else {
                    map.remove(ch);
                }
            }
        }

        return map.size() == 0;
    }
};
```



