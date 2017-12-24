Implement[strStr\(\)](http://www.cplusplus.com/reference/cstring/strstr/).

Return the index of the first occurrence of needle in haystack, or**-1**if needle is not part of haystack.

**Example 1:**

```
Input: haystack = "hello", needle = "ll"
Output:2
```

**Example 2:**

```
Input: haystack = "aaaaa", needle = "bba"
Output:-1
```

For a given source string and a target string, you should output the **first **index\(from 0\) of target string in source string.

If target does not exist in source, just return`-1`.

Have you met this question in a real interview?

Yes

**Clarification**

Do I need to implement KMP Algorithm in a real interview?

* Not necessary. When you meet this problem in a real interview, the interviewer may just want to test your basic implementation ability. But make sure you confirm with the interviewer first.

**Example**

If source =`"source"`and target =`"target"`, return`-1`.

If source =`"abcdabcdefg"`and target =`"bcd"`, return`1`.

[**Challenge**](http://www.lintcode.com/en/problem/strstr/#challenge)

O\(n2\) is acceptable. Can you implement an O\(n\) algorithm? \(hint:_KMP_\)

**Approach: KMP**

```java
public class Solution {
    /*
     * @param source: source string to be scanned.
     * @param target: target string containing the sequence of characters to match
     * @return: a index to the first occurrence of target in source, or -1  if target is not part of source.
     */
    public int strStr(String source, String target) {
        if (source == null || target == null) {
            return -1;
        }
        if (source.length() == 0 && target.length() == 0) {
            return 0;
        }

        if (target.length() == 0) {
            return 0;
        }


        int[] lsp = lspTable(target); 
        int j = 0; // for target indicies 

        for (int i = 0; i < source.length(); i++) {
            while (j > 0 && source.charAt(i) != target.charAt(j)) {
                j = lsp[j-1];
            }

            if (source.charAt(i) == target.charAt(j)) {
                j++;

                if (j == target.length()) {
                    return i+1-j;
                }
            }
        }

        return -1;
    }

    public int[] lspTable(String target) {
        int[] table = new int[target.length()];

        for (int i = 1; i < target.length(); i++) {
            int j = table[i-1]; // previous value


            while (j > 0 && target.charAt(i) != target.charAt(j)) {
                j = table[j-1];
            }

            if (target.charAt(i) == target.charAt(j)) {
                j++;
            }

            table[i] = j;
        }


        return table;
    }
}
```



