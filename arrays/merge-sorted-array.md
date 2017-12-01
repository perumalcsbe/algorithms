Given two sorted integer arrays A and B, merge B into A as one sorted array.

##### Notice

You may assume that A has enough space \(size that is greater or equal to_m_+_n_\) to hold additional elements from B. The number of elements initialized in A and B are _m _and _n _respectively.



**Example**

A =`[1, 2, 3, empty, empty]`, B =`[4, 5]`

After merge, A will be filled as`[1, 2, 3, 4, 5]`



```java
public class Solution {
    /*
     * @param A: sorted integer array A which has m elements, but size of A is m+n
     * @param m: An integer
     * @param B: sorted integer array B which has n elements
     * @param n: An integer
     * @return: nothing
     */
    public void mergeSortedArray(int[] A, int m, int[] B, int n) {
        int pos = m + n - 1;
        int r1 = m - 1;
        int r2 = n - 1;
        
        while (pos >= 0) {
            if (r2 >= 0 && r1 >= 0 && B[r2] >= A[r1]) {
                A[pos] = B[r2];
                r2--; 
            } else if (r1 >= 0) {
                A[pos] = A[r1];
                r1--;
            } else if (r2 >= 0) {
                A[pos] = B[r2];
                r2--;
            }
            
            pos--;
        }
    }
}
```



