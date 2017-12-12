Given an array of characters, compress it [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm).

The length after compression must always be smaller than or equal to the original array.

Every element of the array should be a**character**\(not int\) of length 1.

After you are done **modifying the input array **[**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm), return the new length of the array.

**Example 1:**

```
Input: ["a","a","b","b","c","c","c"]
Output: Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]
Explanation: "aa" is replaced by "a2". "bb" is replaced by "b2". "ccc" is replaced by "c3".
```

**Example 2:**

```
Input: ["a"]
Output: Return 1, and the first 1 characters of the input array should be: ["a"]
Explanation: Nothing is replaced.
```

**Example 3:**

```
Input:

["a","b","b","b","b","b","b","b","b","b","b","b","b"]


Output:

Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].


Explanation:

Since the character "a" does not repeat, it is not compressed. "bbbbbbbbbbbb" is replaced by "b12".
Notice each digit has it's own entry in the array.

```

**Note:**

1. All characters have an ASCII value in`[35, 126]`
2. `1 <= len(chars) <= 1000`

```java
class Solution {
    public int compress(char[] chars) {
        if (chars == null || chars.length < 1) {
            return 0;
        }
        
        StringBuilder res = new StringBuilder();
        int len = chars.length;
        char prev = chars[0];
        int count = 1;
        char cur = Character.MIN_VALUE;
        res.append(prev);
        for (int i = 1; i < len; i++) {
            cur = chars[i];
            if (prev == cur) {
                count++;
            } else {
                if (count > 1 && count < 10) {
                    res.append(count);
                } else if (count > 9) {
                    res.append(count/10);
                    res.append(count%10);
                }
                prev = cur;
                res.append(prev);
                count = 1;
            }
            
        }
        if (cur == prev) {
            if (count > 1 && count < 10) {
                res.append(count);
            } else if (count > 9) {
                res.append(count/10);
                res.append(count%10);
            }
        }
        
        if (res.length() <= len) {
            
            for (int j = 0; j < res.length(); j++) {
                chars[j] = res.charAt(j);
            }
            
            return res.length();
        }
        
        return len;
    }
}
```

**Follow up:**  
Could you solve it using only O\(1\) extra space?

