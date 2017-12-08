Follow up for "Unique Paths":

Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as`1`and`0`respectively in the grid.

##### Notice

m and n will be at most 100.

**Example**

For example,

There is one obstacle in the middle of a 3x3 grid as illustrated below.

```
[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
```

The total number of unique paths is`2`.

**Approach: Dynamic Programming**

```java
public class Solution {
    /*
     * @param obstacleGrid: A list of lists of integers
     * @return: An integer
     */
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
       // base case
       if (obstacleGrid == null || obstacleGrid.length == 0 || obstacleGrid[0].length == 0) {
           return 0;
       }

       int rows = obstacleGrid.length; // rows
       int cols = obstacleGrid[0].length; // columns

       // check frist & last element is 1
       if (obstacleGrid[0][0] == 1 || obstacleGrid[rows - 1][cols - 1] == 1) {
           return 0;
       }

       int[][] dp = new int[rows][cols];
       dp[0][0] = 1;

        // fill top row
       for (int col = 1; col < cols; col++) {
           if (obstacleGrid[0][col] == 1) {
               dp[0][col] = 0;
           } else {
               dp[0][col] = dp[0][col - 1];
           }
       }

       // fill left col
       for (int row = 1; row < rows; row++) {
           if (obstacleGrid[row][0] == 1) {
               dp[row][0] = 0;
           } else {
               dp[row][0] = dp[row - 1][0];
           }
       }

       for (int row = 1; row < rows; row++) {
           for (int col = 1; col < cols; col++) {
               if (obstacleGrid[row][col] == 1) {
                   dp[row][col] = 0;
               } else {
                   dp[row][col] = dp[row - 1][col] + dp[row][col - 1];
               }
           }
       }

       return dp[rows - 1][cols - 1];
    }
}
```



