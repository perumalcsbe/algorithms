Rotate an array ofnelements to the right by **k** steps.

For example, with n= 7 and k= 3, the array`[1,2,3,4,5,6,7]`is rotated to`[5,6,7,1,2,3,4]`.

**Note: **Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.

**Hint: **Could you do it in-place with O\(1\) extra space?

  
**Approach:  ArrayCopy**

```
A [1,2,3,4,5,6,7] k = 3
1. create new array B
2. add 3 elements from end
3. add n-3 elements from begining
4. modify original array
// System.arraycopy(A, 0, B, 0, n);
Time Complexity: O(n) Space Complexity: O(n)
```

```java
class Solution {
    public void rotate(int[] nums, int k) {
        // base case
        if (k == 0 || nums.length < 2) {
            return;
        }
        
        // case where k > nums length
        if (k > nums.length) {
            k = k%nums.length;
        }
        int n = nums.length;
        int[] temp = new int[n];
        
        for (int i = 0; i < k; i++) {
            temp[i] = nums[n-k+i];
        }
        int j = 0;
        for (int i = k; i < n; i++) {
            temp[i] = nums[j];
            j++;
        }
        
        System.arraycopy(temp, 0, nums, 0, n);
    }
}
```



