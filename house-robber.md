You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and**it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight **without alerting the police**.

**Example**

Given`[3, 8, 4]`, return`8`.

**Approach: Dynamic Programming**

```java
public class Solution {
    /*
     * @param A: An array of non-negative integers
     * @return: The maximum amount of money you can rob tonight
     */
    public long houseRobber(int[] A) {
        // base case
        if (A == null || A.length < 1) return 0;
        
        int n = A.length;
        long[] dp = new long[n + 1];
        dp[0] = 0;
        dp[1] = A[0];
        
        for (int i = 2; i <= n; i++) {
            dp[i] = Math.max(dp[i - 1], A[i-1] + dp [i - 2]);
        }
        
        return dp[n];
    }
}
```

[**Challenge**](http://www.lintcode.com/en/problem/house-robber/#challenge)

O\(n\) time and O\(1\) memory.

```java
public class Solution {
    /*
     * @param A: An array of non-negative integers
     * @return: The maximum amount of money you can rob tonight
     */
    public long houseRobber(int[] A) {
        // base case
        if (A == null || A.length < 1) return 0;
        
        int n = A.length;
        long a = 0; // n-2
        long b = A[0]; // n -1
        long c = A[0]; // if array has 1 element
        
        for (int i = 2; i <= n; i++) {
            c = Math.max(b, A[i - 1] + a);
            a = b;
            b = c;
        }
        
        return c;
    }
}
```



