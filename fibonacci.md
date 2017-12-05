Find the\_N\_th number in Fibonacci sequence.

A Fibonacci sequence is defined as follow:

* The first two numbers are 0 and 1.
* The _i\_th number is the sum of \_i_-1 th number and _i_-2 th number.

The first ten numbers in Fibonacci sequence is:

`0, 1, 1, 2, 3, 5, 8, 13, 21, 34 ...`

##### Notice

The\_N\_th fibonacci number won't exceed the max value of signed 32-bit integer in the test cases.

**Example**

Given`1`, return`0`

Given`2`, return`1`

Given`10`, return`34`

**Approach: Recursive O\(n!\)**

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

**Approach: Dynamic Programming O\(n\) Space Complexity O\(n\)**

```java
public class Solution {
    /*
     * @param n: an integer
     * @return: an ineger f(n)
     */
    public int fibonacci(int n) {
        int[] cache = new int[n+1];
        cache[0] = 0;
        cache[1] = 1;
        for (int i = 2; i <= n; i++) {
            cache[i] = cache[i - 1] + cache[i - 2];
        }


        return cache[n - 1];
    }
}
```

**Approach: optimized Space Complexity**

```java
public class Solution {
    /*
     * @param n: an integer
     * @return: an ineger f(n)
     */
    public int fibonacci(int n) {
        int a = 0;
        int b = 1;
        int c;
        if (n < 2) {
            return a;
        }
        for (int i = 2; i < n; i++) {
            c = b + a;
            a = b;
            b = c;
        }


        return b;
    }
}
```



