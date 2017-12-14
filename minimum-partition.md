Given a set of integers, write a function to divide it into two sets S1 and S2 such that the absolute difference between their sums is minimum.

If there is a set`S`with`n`elements, then if we assume Subset1 has`m`elements, Subset2 must have`n-m`elements and the value of`abs(sum(Subset1) – sum(Subset2))`should be minimum.

**Example**

```
Given nums = [1, 6, 11, 5], return 1

// Subset1 = [1, 5, 6], sum of Subset1 = 12 
// Subset2 = [11], sum of Subset2 = 11   
// abs(11 - 12) = 1     
```

```
for E[i:] either can be included in subset or excluded in subset based on remaining E[i+1...n] sum
 base case: n < 0         
          minP(s, 3, 0, 0)
          
          
  minP(s, 2, 5, 0)  minP(s, 2, 0, 5)
        /                 \
   minP(s, 1, 7, 0)       minP(s, 1, 0, 7)
      /                     \  
   minP(s, 0, 18, 0)      minP(s, 0, 0, 
```

```java
public class Solution {
    /*
     * @param : the given array
     * @return: the minimum difference between their sums 
     */
    public int findMin(int[] arr) {
        //base case
        
        return findMin(arr, arr.length-1, 0, 0);
    }
    
    private int findMin(int[] arr, int n, int s1, int s2) {
        // base case
        if (n < 0) {
            return Math.abs(s1-s2);
        }
        
        // include in s1
        int include = findMin(arr, n-1, s1+arr[n], s2);
        // exclude in s1
        int exclude = findMin(arr, n-1, s1, s2+arr[n]);
        
        return Math.min(include, exclude);
    }
}
```



