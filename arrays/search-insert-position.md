Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume**NO**duplicates in the array.

**Example**

`[1,3,5,6]`, 5 → 2

`[1,3,5,6]`, 2 → 1

`[1,3,5,6]`, 7 → 4

`[1,3,5,6]`, 0 → 0

**Approach: Linear search O\(n\)**

```java
public class Solution {
    /*
     * @param A: an integer sorted array
     * @param target: an integer to be inserted
     * @return: An integer
     */
    public int searchInsert(int[] A, int target) {
        if (A == null || A.length == 0) return 0;
        for (int i = 0 ; i < A.length; i++) {
            if (i == 0 && A[i] > target || A[i] == target) {
                return i;
            } if (A[i] < target && i + 1 < A.length && A[i + 1] > target) {
                return i + 1;
            }
        }
        
        return A.length;
    }
}
```

**Approach: Binary Search O\(logn\)**



