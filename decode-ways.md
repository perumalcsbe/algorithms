A message containing letters from`A-Z`is being encoded to numbers using the following mapping:

```
'A' ->1
'B' ->2
...
'Z' ->26

```

Given an encoded message containing digits, determine the total number of ways to decode it.

**Example**

Given encoded message`12`, it could be decoded as`AB`\(1 2\) or`L`\(12\).  
The number of ways decoding`12`is 2.

  


|  | 0 | 1 | 2 |
| :--- | :--- | :--- | :--- |
| "11" =&gt; dp\[1\] =&gt;2 | 1 | 2 |  |
| "111"=&gt;dp\[2\] =&gt;3 | 1 | 2 | 3 |
| "120"=&gt;dp\[2\] =&gt;4 | 1 | 2 | 4 |

```java
public class Solution {
    /*
     * @param s: a string,  encoded message
     * @return: an integer, the number of ways decoding
     */
    public int numDecodings(String s) {
        
        if (s == null || s.length() < 1 || s.charAt(0) == '0') {
            return 0;
        }
        
        int len = s.length();
        
        // return 1 if number 1-9
        if (len == 1) {
            return 1;
        }
        
        // memorization 
        int[] dp = new int[len+1];
        
        // initialize 0 with 1 for 1-9
        dp[0] = 1;
        
        // number greater than 26
        if (Integer.parseInt(s.substring(0, 2)) > 26) {
            // 1 if d == 0
            // 2 if d != 2
            dp[1] = (s.charAt(1) == '0') ? 0 : 1;
        } else {
            // number between 10 - 26
            // 1 if d == 1
            // 2 if d != 2
            dp[1] = (s.charAt(1) == '0') ? 1 : 2;
        }
        
        // for number greater than 26
        for (int i = 2; i < len; i++) {
            // dp[i] = dp[i] + dp[i-1] if s.charAt(i) != 0
            if (s.charAt(i) != '0') {
                dp[i] += dp[i-1];
            }
            
            // check two digits at ith position
            int x = Integer.parseInt(s.substring(i-1, i+1));
            if (x <= 26 && x >=10) {
                dp[i] += dp[i-2];
            }
            
        }
        
        
        return dp[len-1];
        
    }
}
```



