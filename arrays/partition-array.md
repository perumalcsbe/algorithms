Given an array`nums`of integers and an int`k`, partition the array \(i.e move the elements in "nums"\) such that:

* All elements &lt; _k \_are moved to the \_left_
* All elements &gt;= _k \_are moved to the \_right_

Return the partitioning index, i.e the first index_i\_nums\[\_i_\] &gt;=_k_.

##### Notice

You should do really partition in array\_nums\_instead of just counting the numbers of integers smaller than k.

If all elements in_nums\_are smaller than\_k_, then return _nums.length_

**Example**

If nums =`[3,2,2,1]`and`k=2`, a valid answer is`1`.

[**Challenge**](http://www.lintcode.com/en/problem/partition-array/#challenge)

Can you partition the array in-place and in O\(n\)?

##### Approach: Two Pointers

```
public class Solution {
    /*
     * @param nums: The integer array you should partition
     * @param k: An integer
     * @return: The index after partition
     */
    public int partitionArray(int[] nums, int k) {
        // do boundry check
        if (nums == null || nums.length == 0) return 0; 
        int left = 0;
        int right = nums.length - 1;
        int i = 0;
        while(i <= right) {
            if (nums[i] < k) {
                swap(nums, i, left);
                left++;
                i++;
            } else if (nums[i] > k) {
                swap(nums, i, right);
                right--;
            } else {
                i++;
            }
        }

        return left;
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```



