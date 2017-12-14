There is a fence with`n`posts, each post can be painted with one of the`k`colors.  
You have to paint all the posts such that no more than two adjacent fence posts have the same color.  
Return the total number of ways you can paint the fence.

##### Notice

`n`and`k`are non-negative integers.

**Example**

Given`n`=3,`k`=2 return 6

```
      post 1,   post 2, post 3
way1    0         0       1     
way2    0         1       0
way3    0         1       1
way4    1         0       0
way5    1         0       1
way6    1         1       0
```

**Approach: Greedy**

```java
public class Solution {
    /*
     * @param n: non-negative integer, n posts
     * @param k: non-negative integer, k colors
     * @return: an integer, the total number of ways
     */
    public int numWays(int n, int k) {
        // base case: if no posts
        if (n == 0) {
            return 0;
        } 
        
        // if there is one post
        // p1 (k1, k2)      => 2
        // p1 (k1, k2, k3)  => 3
        // p1 (k1, k2,,,kn) => k
        // then k possible colors can be painted
        if (n == 1) {
            return k;
        }
        
        // if there are 2 posts and 2 colors
        // (k1, k1) (k1, k2) (k2, k1) (k2, k2)
        // then (same color k = 2 + different color k*(k-1) => 2) * (k-1) => 4
        // if there are 3 posts and 2 colors
        // (k1, k1, k2) 
        // (k1, k2, k1)
        // (k1, k2, k2)
        // (k2, k1, k1) 
        // (k2, k1, k2)
        // (k2, k2, k1)
        // then (same color k => 2 + different color k*(k-1) => 2) * (k-1) => 4 + 2 => 6 
        // if there are 3 posts and 3 colors
        // (k1, k1, k2)
        // (k1, k2, k3) 
        // (k1, k3, k1) 
        // (k2, k2) (k2, k1) (k2, k3) 
        // (k3, k3) (k3, k1) (k3, k1)
        // then (same color k => 3 + different color k*(k-1) => 6) * (k-1) => 18 + 6 => 24
        int different = k*(k-1);
        int same = k;
        for (int i = 2; i <n; i++) {
            int t = different;
            different = (same+different)*(k-1);
            same = t;
        }
        
        return same + different;
    }
}
```

**Approach: Recursion **

```
Consider E as posts and K as colors.

for E[i:],either 
   1. k[j:] can be included if E[i-1] or E[i-2] is not k[j] 
   2. k[j:] can be excluded if E[i-1] or E[i-2] is k[j] 
E[0] = 0
E[1] = 2   => i*k
     - k[0]
     - k[1]
E[2]  = 4  => i* k
     - k[0] if E[0] == k[0]
     - k[0] if E[0] == k[1]
     - k[1] if E[0] == k[0]
     - k[1] if E[0] == k[1]
E[3]  = 6  => i* k
     - k[0] if E[0] == k[0] && E[1] == k[1]
     - K[0] if E[0] == k[1] && E[1] == k[0]
     - K[0] if E[0] == k[1] && E[1] == k[1]
     - k[1] if E[0] == k[0] && E[1] == k[1]
     - k[1] if E[0] == k[1] && E[1] == k[0]
     - k[1] if E[0] == k[0] && E[1] == k[0]      
     
E[n] = n* k 

n = 3 & k = 3
   E1     E2      E3
1  0      0       1
2  0      0       2
3  0      1       0
4  0      2       0
5  0      1       1
6  0      2       2
7  1       
```

**Approach: Dynamic Programming**

```
[0, 2, ]

k = 4, k = 2
    post 1,   post 2, post 3, post 4
way1    0         0       1      0
way2    0         1       0      1
way3    0         1       1      0
way4    1         0       0      1
way5    1         0       1      0
way6    1         1       0      0

```



