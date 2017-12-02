Given a string of numbers, write a function to find the maximum value from the string, you can add a`+`or`*`sign between any two numbers.



**Example**

Given str =`01231`, return`10`  
`((((0 + 1) + 2) * 3) + 1) = 10`we get the maximum value 10

Given str =`891`, return`73`  
As 8 \* 9 \* 1 = 72 and 8 \* 9 + 1 = 73 so 73 is maximum.



```java
public class Solution {
    /*
     * @param : the given string
     * @return: the maximum value
     */
    public int calcMaxValue(String str) {
        int res = 0;
        
        for (Character ch : str.toCharArray()) {
            int n = ch - '0';
            if (n < 2 || res < 2) {
                res += n;
            } else {
                res *= n;
            }
        }
        
        return res;
    }
};
```



