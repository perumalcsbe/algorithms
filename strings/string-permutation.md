Given two strings, write a method to decide if one is a permutation of the other.

**Example**

`abcd`is a permutation of`bcad`, but`abbe`is not a permutation of`abe`

```java
public class Solution {
    /*
     * @param A: a string
     * @param B: a string
     * @return: a boolean
     */
    public boolean Permutation(String A, String B) {
        if (A.length() != B.length()) return false;

        Map<Character, Integer> map = new HashMap<>();

        for(Character ch : A.toCharArray()) {
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }

        for(Character ch : B.toCharArray()) {
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
}
```

```
Time complexity: O(N+M)
Space Complexity: O(1)
```



