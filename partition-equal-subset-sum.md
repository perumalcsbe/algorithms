Given a`non-empty`array containing`only positive integers`, find if the array can be partitioned into`two`subsets such that the sum of elements in both subsets is equal.

##### Notice

Each of the array element will not exceed 100.  
The array size will not exceed 200.

**Example**

Given nums =`[1, 5, 11, 5]`, return`true`  
two subsets: \[1, 5, 5\], \[11\]

Given nums =`[1, 2, 3, 9]`, return`false`



**Approach: Recursive **

* Base case: return false if array length &lt; 2 
* return false if array sum %2 != 0 \(odd\)
  * continue otherwise 
* take half of sum \(since sum is even sum/2\)
  * for each number, check whether if include then calculate remaining sum recursively 
  * for each number, check whether if exclude then calculate remaining sum recursively

```java
public class Solution {
    /*
     * @param nums: a non-empty array only positive integers
     * @return: true if can partition or false
     */
    public boolean canPartition(int[] nums) {
        // base case
        if (nums == null || nums.length < 2) {
            return false;
        }
        // step1: Caculate sum
        int sum = 0;
        for (int n : nums) {
            sum += n;
        }
        // step2: if sum is odd then return false
        if (sum%2 != 0) {
            return false;
        }
        
        return canPartition(nums, 0, sum);
        
    }
    
    private boolean canPartition(int[] nums, int i, int sum) {
        // Exit case 1: sum becomes 0
        if (sum == 0) {
            return true;
        }
        
        // Exit case 2: sum is below 0 or no more elements in array
        if (i > nums.length-1 || sum < 0) {
            return false;
        }
        
        // for each number in an array
        // step1: include and subtract from sum and then calculate remaining sum
        boolean include = canPartition(nums, i + 1, sum-nums[i]);
        // step2: exclude and calculate sume
        boolean exclude = canPartition(nums, i + 1, sum);
        
        // step3: any one true then return true
        return include || exclude;
    }
}
```

**Approach: Memorization**





