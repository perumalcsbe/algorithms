Given two strings, find the longest common subsequence \(_LCS_\).

Your code should return the length of_LCS_.

**Clarification**

What's the definition of Longest Common Subsequence?

* [https://en.wikipedia.org/wiki/Longest\_common\_subsequence\_problem](https://en.wikipedia.org/wiki/Longest_common_subsequence_problem)
* [http://baike.baidu.com/view/2020307.htm](http://baike.baidu.com/view/2020307.htm)

**Example**

For`"ABCD"`and`"EDCA"`, the\_LCS\_is`"A"`\(or`"D"`,`"C"`\), return`1`.

For`"ABCD"`and`"EACB"`, the\_LCS\_is`"AC"`, return`2`.

##### Approach: Recursive O\(2^mn\)

```java
public class Solution {
    /*
     * @param A: A string
     * @param B: A string
     * @return: The length of longest common subsequence of A and B
     */
    public int longestCommonSubsequence(String A, String B) {
        return longestCommonSubsequence(A, B, A.length(), B.length());
    }

    private int longestCommonSubsequence(String A, String B, int m, int n) {
        // base case
        // if we are end of any of the string then stop
        if (m == 0 || n == 0) {
            return 0;
        }

        // if last charactor of both Strings matches
        if (A.charAt(m - 1) == B.charAt(n - 1)) {
            return longestCommonSubsequence(A, B, m - 1, n - 1) + 1;
        }


        return Math.max(longestCommonSubsequence(A, B, m - 1, n), longestCommonSubsequence(A, B, m, n - 1));

    }
}
```

**Approach: Dynamic Programming O\(n\)**

```java
public class Solution {
    /*
     * @param A: A string
     * @param B: A string
     * @return: The length of longest common subsequence of A and B
     */
    public int longestCommonSubsequence(String A, String B) {
        int m = A.length();
        int n = B.length();
        int[][] dp = new int[m + 1][n + 1]; // by default filled with 0
        return longestCommonSubsequence(A, B, m, n, dp);
    }

    private int longestCommonSubsequence(String A, String B, int m, int n, int[][] dp) {
        // base case
        // if we are end of any of the string then stop
        if (m == 0 || n == 0) {
            return 0;
        }

        // if subproblem not found in dp then calculate and store the results
        if (dp[m][n] == 0) {
            // if last charactor of both Strings matches
            if (A.charAt(m - 1) == B.charAt(n - 1)) {
                dp[m][n] = longestCommonSubsequence(A, B, m - 1, n - 1, dp) + 1;
            } else {

                dp[m][n] = Math.max(longestCommonSubsequence(A, B, m - 1, n, dp), longestCommonSubsequence(A, B, m, n - 1, dp));
            }
        }

        // if subproblem found in dp then return it
        return dp[m][n];

    }
}
```



