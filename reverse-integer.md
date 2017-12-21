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
0. result = 0;
1. do num mod 10 and store remainder and divide num by 10 until num is 0
2. new result = result * 10 + remainder   
3. overflow case: return 0 if previous value is not matching then overflow occured  (new result - remainder)/10 != res)

for e.g. 123
res = 0
num       rem   rev                    
123%10 => 3      0*10 + 3 => 3 
123/10    
12%10  => 2      3*10 + 2 => 32
12/10
1%10   => 1      32*10 + 1 => 321 
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



