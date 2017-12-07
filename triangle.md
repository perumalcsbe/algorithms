Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.  
**Notice**

Bonus point if you are able to do this using only O\(n\) extra space, where n is the total number of rows in the triangle.

**Example**

Given the following triangle:

```
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
```

The minimum path sum from top to bottom is 11 \(i.e., 2 + 3 + 5 + 1 = 11\).

**Approach: Recursive **

```
Time Complexity: O(2^n)
space Complexity: O(n)
```

![](/assets/traingle.png)

> top down fashion

```java
public class Solution {
    /*
     * @param triangle: a list of lists of integers
     * @return: An integer, minimum path sum
     */
    public int minimumTotal(int[][] triangle) {
        // base case
        if (triangle == null || triangle.length < 1 || triangle[0].length < 1) {
            return 0;
        }

        if (triangle.length == 1 && triangle[0].length == 1) {
            return triangle[0][0];
        }

        return minimumTotal(triangle, 0, 0);
    }


    private int minimumTotal(int[][] triangle, int i, int j) {
        int m = triangle.length-1;
        int n = triangle[i].length-1;
        // base case
        // if we reach bottom row
        if (i + 1 > m) {
            return triangle[i][j];
        }

        return triangle[i][j] + Math.min(
                minimumTotal(triangle, i+1, j), 
                minimumTotal(triangle, i+1, j+1)
                );
    }
}
```

**Approach: Dynamic Programming**

```
Time Complexity: O(n)
Space Complexity: O(n)
```

| dp\[\] | 0 | 1 | 2 | 3 |
| :--- | :--- | :--- | :--- | :--- |
| fill bottom row | 4 | 1 | 8 | 3 |
| i = 2 | 7 min\(t:4,dp\[0+1\]:1\)+6 | 6 min\(1,8\)+5 | 10 min\(8, 3\) +7 |  |
| i = 1 | 9 min\(7,6\)+3 | 10 min\(6,10\)+4 |  |  |
| i = 0 | 11 min\(9, 10\)+2 |  |  |  |

```java
public class Solution {
    /*
     * @param triangle: a list of lists of integers
     * @return: An integer, minimum path sum
     */
    public int minimumTotal(int[][] triangle) {
        // base case
        if (triangle == null || triangle.length < 1 || triangle[0].length < 1) {
            return 0;
        }

        int n = triangle.length;
        int[] dp = new int[n];

        // fill with last row
        for (int i = 0; i < n; i++) {
            dp[i] = triangle[n - 1][i];
        }

        // start from one above last row
        for (int i = n - 2; i >= 0; i--) {
            for (int j = 0; j <= i; j++) {
                dp[j] = Math.min(dp[j], dp[j + 1]) + triangle[i][j];
            }
        }

        return dp[0];
    }
```



