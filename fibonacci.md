Find the_N_th number in Fibonacci sequence.

A Fibonacci sequence is defined as follow:

* The first two numbers are 0 and 1.
* The _i_th number is the sum of _i_-1 th number and _i_-2 th number.

The first ten numbers in Fibonacci sequence is:

`0, 1, 1, 2, 3, 5, 8, 13, 21, 34 ...`

##### Notice

The_N_th fibonacci number won't exceed the max value of signed 32-bit integer in the test cases.

**Example**

Given`1`, return`0`

Given`2`, return`1`

Given`10`, return`34`



```java
public class Solution {
    /*
     * @param n: an integer
     * @return: an ineger f(n)
     */
    public int fibonacci(int n) {
       if (n < 2) return 0;
       if (n == 2) return 1;
       
       return fibonacci(n - 1) + fibonacci(n - 2);
    }
}
```



