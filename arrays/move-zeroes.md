Given an array`nums`, write a function to move all`0`'s to the end of it while maintaining the relative order of the non-zero elements.

For example, given`nums = [0, 1, 0, 3, 12]`, after calling your function,`nums`should be`[1, 3, 12, 0, 0]`.

**Note**:

1. You must do this **in-place **without making a copy of the array.
2. Minimize the total number of operations.

##### Approach 1: [Two Pointers](/two-pointers.md)

```java
public class Solution {
    /*
     * @param nums: an integer array
     * @return: 
     */
    public void moveZeroes(int[] nums) {
        if (nums == null || nums.length < 2) return;
        int i = 0;
        while (i < nums.length - 1) {
            
            if (nums[i] == 0) {
               
            
                int j = i + 1;
                while (j < nums.length && nums[j] == 0) {
                    j++;
                }
                if (j < nums.length && nums[j] != 0) {
                    swap(nums, i , j);
                }
                
            }
             i++;
        }
    }
    
    private void swap(int[] nums, int i, int j) {
        int t = nums[i];
        nums[i] = nums[j];
        nums[j] = t;
    }
}
```

```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    let i = 0;
    let j = nums.length  - 1;
    while ( i <= j) {
        if (nums[i] === 0) {
            nums.splice(i, 1);
            nums.push(0);
            j--;
        } else {
            i++;
        }
    }
};
```



