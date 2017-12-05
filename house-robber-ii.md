After robbing those houses on that street, the thief has found himself a new place for his thievery so that he will not get too much attention. This time, all houses at this place are **arranged in a circle**. That means the first house is the neighbor of the last one. Meanwhile, the security system for these houses remain the same as for those in the previous street.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight **without alerting the police**.

##### Notice

This is an extension of [House Robber](http://www.lintcode.com/problem/house-robber/).

**Example**

nums =`[3,6,4]`, return`6`

**Approach: Dynamic Programming**

```java
public class Solution {
    /*
     * @param nums: An array of non-negative integers.
     * @return: The maximum amount of money you can rob tonight
     */
    public int houseRobber2(int[] nums) {
        // base case
        if (nums == null || nums.length < 1) {
            return 0;
        }

        if (nums.length == 1) {
            return nums[0];
        }

        int n = nums.length;

        int include = helper(nums, 0, n - 2);
        int exclude = helper(nums, 1, n - 1);

        return Math.max(include, exclude);
    }

    public int helper(int[] nums, int i, int n) {
        if (i == n) {
            return nums[i];
        }
        int a = nums[i];
        int b = Math.max(nums[i + 1], a); // if array has 1 element
        int c = nums[i];
        for (int k = i + 2; k <= n; k++) {
            c = Math.max(b, nums[k] + a);
            a = b;
            b = c;
        }

        return c;
    }
}
```



