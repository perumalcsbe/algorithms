Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return`-1`.

**Example**

Given s =`"lintcode"`, return`0`.

Given s =`"lovelintcode"`, return`2`.

**Approach: Two Loops **

```
Run time complexity: O(n^2)
Space complexity: O(1)
```

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

**Approach: HashMap **

```
run time complexity: O(n) 
space complexity: O(1)
```

> use hasmp to store index & count, increment count and index if encounter duplicates. finally return lower index for count 1

example: "abcab"

| Character | a | b | c |
| :--- | :--- | :--- | :--- |
| Pair&lt;int, int&gt; | index: 3, count: 2 | index: 4, count: 2 | index: 2, count: 1 |

```java
public class Solution {
    private class Pair {
        int index, count;

        public Pair(int index, int count) {
            this.index = index;
            this.count = count;
        }
    }
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
        HashMap<Character, Pair> map = new HashMap<>();

        for (int i = 0; i < n; i++) {
            char ch = s.charAt(i);

            if (map.containsKey(ch)) {
                Pair x = map.get(ch);
                map.put(ch, new Pair(i, x.count+1));
            } else {
                map.put(ch, new Pair(i, 1));
            }
        }

        int max = Integer.MAX_VALUE;
        for (Map.Entry<Character, Pair> entry : map.entrySet()) {
            Pair x = entry.getValue();
            if (x.count == 1) {
                max = Math.min(max, x.index);
            }
        }


        return max < Integer.MAX_VALUE ? max : result;
    }
}
```



