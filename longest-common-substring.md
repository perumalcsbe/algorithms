Given two strings, find the longest common substring.

Return the length of it.

##### Notice

The characters in **substring **should occur continuously in original string. This is different with**subsequence**.

**Example**

```
Given A ="ABCD", B ="CBCE", return 2.
```

[**Challenge**](http://www.lintcode.com/en/problem/longest-common-substring/#challenge)

O\(n x m\) time and memory.

**Approach: Dynamic Programming O\(m\*n\)**

```java
public class Solution {
    /*
     * @param A: A string
     * @param B: A string
     * @return: the length of the longest common substring.
     */
    public int longestCommonSubstring(String A, String B) {
        int result = 0;
        if (A == null || B == null || A.length() < 1 || B.length() < 1) {
            return result;
        }
        int m = A.length();
        int n = B.length();
        int[][] dp = new int[m + 1][n + 1];
        
        // filling dp with bottom up fashion
        for (int i = 0; i <= m; i++) {
            for (int j = 0; j <= n; j++) {
                
                // base case for first row or first coloumn fill with 0
                if (i == 0 || j == 0) {
                    dp[i][j] = 0;
                } else if (A.charAt(i - 1) == B.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                    result = Math.max(result, dp[i][j]);
                } else {
                    dp[i][j] = 0;
                }
                
            }
        }
        
        
        return result;
    }
}
```



