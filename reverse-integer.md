Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**

```
Input: 123
Output: 321
```

**Example 2:**

```
Input:-123
Output:-321
```

**Example 3:**

```
Input: 120
Output:21
```

**Note:**  
Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

**Approach: Mod**

```
1. if number is negative then convert to positive by -1 * num and set boolean isNegative = true
2. do mod 10 and store remainder and divide by 10 until 0
         2.1. if remainder is 0 skip it
3. add remainder * 10 if > 0   

for e.g. 123
num       rem   rev                    
123%10 => 3      3*10 => 30 
123/10    
12%10  => 2      2*10 => 
12/10
1%10   => 1   
1/10 => 0 stop
   

```

```java
class Solution {
    public int reverse(int x) {
        int res = 0;
        
        while (x != 0) {
            int rem = x % 10;
            // overflow check
            int rev = res * 10 + rem;
            if ((rev-rem) / 10 != res) {
                return 0;
            }
            
            res = rev;
            x = x / 10;
        }
        
        return res;
    }
}
```



