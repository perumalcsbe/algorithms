Merge two given sorted integer array _A _and _B _into a new sorted integer array.



**Example**

A=`[1,2,3,4]`

B=`[2,4,5,6]`

return`[1,2,2,3,4,4,5,6]`

[**Challenge**](http://www.lintcode.com/en/problem/merge-two-sorted-arrays/#challenge)

How can you optimize your algorithm if one array is very large and the other is very small?



```java
public class Solution {
    /*
     * @param A: sorted integer array A
     * @param B: sorted integer array B
     * @return: A new sorted integer array
     */
    public int[] mergeSortedArray(int[] A, int[] B) {
        
        int[] result = new int[A.length + B.length];
        int l1 = 0;
        int l2 = 0;
        int i = 0;
        while (l1 < A.length || l2 < B.length) {
            if (l1 < A.length && l2 < B.length && A[l1] < B[l2]) {
                result[i] = A[l1];
                l1++;
            } else if (l1 < A.length && l2 == B.length) {
                result[i] =  A[l1];
                l1++;
            } else if (l2 < B.length) {
                result[i] = B[l2];
                l2++;
            }
            
            i++;
        }
        
        return result;
    }
}
```



