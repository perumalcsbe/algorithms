There is an integer array which has the following features:

* The numbers in adjacent positions are different.
* A\[0\] &lt; A\[1\] && A\[A.length - 2\] &gt; A\[A.length - 1\].

We define a position P is a peek if:

```
A[P] >A[P-1] && A[P] > A[P+1]
```

Find a peak element in this array. Return the index of the peak.

##### Notice

* It's guaranteed the array has at least one peak.
* The array may contain multiple peeks, find any of them.
* The array has at least 3 numbers in it.

**Example**

Given`[1, 2, 1, 3, 4, 5, 7, 6]`

Return index`1`\(which is number 2\) or`6`\(which is number 7\)

[**Challenge**](http://www.lintcode.com/en/problem/find-peak-element/#challenge)

Time complexity O\(logN\)

```java
public class Solution {
    /*
     * @param A: An integers array.
     * @return: return any of peek positions.
     */
    public int findPeak(int[] A) {
        int l = 0;
        int r = A.length - 1;
        
        while(l < r) {
            int mid = (l + r) / 2; 
            
            // check if mid is peak then return it
            if (A[mid - 1] < A[mid] && A[mid] > A[mid + 1]) {
                return mid;
            } else if (A[mid - 1] > A[mid]) {
                r = mid;
            } else {
                l = mid;
            }
        }
        
        return -1;
    }
}
```



