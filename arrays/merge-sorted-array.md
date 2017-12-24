Given two sorted integer arrays A and B, merge B into A as one sorted array.

##### Notice

You may assume that A has enough space \(size that is greater or equal to_m_+_n_\) to hold additional elements from B. The number of elements initialized in A and B are m and n respectively.

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

```js
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
    let end = m + n - 1;
    let end1 = m - 1;
    let end2 = n - 1;
    // traverse from end to 0
    while (end >= 0) {
        // check if nums2 end is greater than equal to nums1 end
        if (end1 >= 0 && end2 >= 0 && nums2[end2] >= nums1[end1]) {
            nums1[end] = nums2[end2];
            end2--;
        } else if (end1 >= 0) { // remaining nums1
            nums1[end] = nums1[end1];
            end1--;
        } else if (end2 >= 0) { // remain nums2
            nums1[end] = nums2[end2];
            end2--;
        }
        end--;
    }
};
```



