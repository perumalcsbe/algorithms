Given a **m x n** grid filled with non-negative numbers, find a path from top left to bottom right which **minimizes** the sum of all numbers along its path.

##### Notice

You can only move either down or right at any point in time.

**Example 1:**

```
[[1,3,1],
 [1,5,1],
 [4,2,1]]
```

Given the above grid map, return`7`. Because the path 1→3→1→1→1 minimizes the sum.

**Approach: Recursive **

> bottom up fashion

![](/assets/minPathSum.png)

| m x n | 0 | 1 | 2 |
| :--- | :--- | :--- | :--- |
| 0 | 1 \(c:1\) | 4 \(p:1+ c:3\) | 5 \(p:4 + c:1\) |
| 1 | 2 \(t:1 + c:1\) | 7 Min\(t:4 +c:5\), \(p: 2 +c:5\) | 6 Min\(t:5+c:1, p:7+c:1\) |
| 2 | 6 \(t:2 + c:4\) | 8 Min\(t:7+c:2, p:6+c:2\) | 7 Min\(t:6+c:1, p:8+c:1\) |

> TOP down Fashion

**Approach: Dynamic Programming**

```
Time Complexity: O(mn)
Space Complexity: O(mn)
```

```java
public class Solution {
    /*
     * @param grid: a list of lists of integers
     * @return: An integer, minimizes the sum of all numbers along its path
     */
    public int minPathSum(int[][] grid) {
        // base case
        if (grid == null || grid.length < 1 || grid[0].length < 1) {
            return 0;
        }

        int m = grid.length;
        int n = grid[0].length;

        int[][] dp = new int[m][n];

        dp[0][0] = grid[0][0];
        // top row
        for (int j = 1; j < n; j++) {
            dp[0][j] = grid[0][j] + dp[0][j - 1];
        }

        //left coloumn
        for (int i = 1; i < m; i++) {
            dp[i][0] = grid[i][0] + dp[i - 1][0];
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[i][j] = Math.min(dp[i][j-1], dp[i-1][j]) + grid[i][j];
            }
        }

        return dp[m - 1][n - 1];
    }
}
```



