Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return`-1`.

**Example**

Given s =`"lintcode"`, return`0`.

Given s =`"lovelintcode"`, return`2`.

**Approach: Two Loops O\(n^2\)**

```java
public class Solution {
    /*
     * @param s: a string
     * @return: it's index
     */
    public int firstUniqChar(String s) {
        int result = -1;
        // base case
        if (s == null || s.length() < 1) {
            return result;
        }
        int n = s.length();
        for (int i = 0; i < n - 1; i++) {

            boolean found = false;
            for (int j = 0; j < n; j++) {
                if (i != j && s.charAt(i) == s.charAt(j)) {
                    found = true;
                }
            }
            if (!found) {
                return i;
            }
        }


        return result;
    }
}
```

**Approach: **

`lovelintcode`

length: 12

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| l | o | v | e | l | i | n | t | c | o | d | e |

Dequeue

| first |  |  |  |  |  |  |  |  |  | last |  |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ~~l~~ | ~~o~~ | v | e | l | i | n | t | c | o | d | e |



