Compare two strings A and B, determine whether A contains all of the characters in B.

The characters in string A and B are all**Upper Case**letters.

##### Notice

The characters of B in A are not necessary continuous or ordered.

**Example**

For`A = "ABCD"`,`B = "ACD"`, return`true`.

For`A = "ABCD"`,`B = "AABC"`, return`false`.



```java
public class Solution {
    /*
     * @param A: A string
     * @param B: A string
     * @return: if string A contains all of the characters in B return true else return false
     */
    public boolean compareStrings(String A, String B) {
        HashMap<Character, Integer> map = new HashMap<>();
        
        for (char a: A.toCharArray()) {
            map.put(a, 1 + map.getOrDefault(a, 0));
        }
        
        for (char b: B.toCharArray()) {
            if (map.containsKey(b)) {
                if (map.get(b) > 1) {
                    map.put(b, map.get(b)-1);
                } else {
                    map.remove(b);
                }
            } else {
                return false;
            }
        }
        
        return true;
    }
}
```



