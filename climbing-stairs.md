You are climbing a stair case. It takes **n** steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Example**

Given an example n=3 , 1+1+1=2+1=1+2=3

return 3

**Approach: Dynamic Programming**

```
public class Solution {
    /**
     * @param n: An integer
     * @return: An integer
     */
    public int climbStairs(int n) {
        if (n == 0) return 0;
        if (n == 1) return 1;
        int[] dp = new int[n + 2];
        dp[0] = 0;
        dp[1] = 1;
        
        for (int i = 2; i <= n + 1; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        
        // 
        return dp[n + 1];
    }
}
```



