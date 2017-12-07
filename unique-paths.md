A robot is located at the top-left corner of a\_m\_x\_n\_grid.

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid.

How many possible unique paths are there?

##### Notice

\_m \_and \_n \_will be at most 100.

**Example**

Given m =`3`and n =`3`, return`6`.  
Given m =`4`and n =`5`, return`35`.

Approach: Dynamic Programming O\(m\*n\)

```java
public class Solution {
    /*
     * @param m: positive integer (1 <= m <= 100)
     * @param n: positive integer (1 <= n <= 100)
     * @return: An integer
     */
    public int uniquePaths(int m, int n) {

        if (m == 0 || n == 0) return 0;
        if (m == 1 || n == 1) return 1;
        int[][] dp = new int[m][n];

        // fill first rows with 1
        for (int col = 0; col < n; col++) {
            dp[0][col] = 1; 
        }

        // fill first coloumn with 1
        for (int row = 0; row < m; row++) {
            dp[row][0] = 1; 
        }

        for (int row = 1; row < m; row++) {
            for (int col = 1; col < n; col++) {
                dp[row][col] = dp[row - 1][col] + dp[row][col - 1];
            }
        }

        return dp[m - 1][n - 1];
    }
}
```



