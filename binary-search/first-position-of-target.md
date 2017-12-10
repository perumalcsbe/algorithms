For a given sorted array \(ascending order\) and a`target`number, find the first index of this number in`O(log n)`time complexity.

If the target number does not exist in the array, return`-1`.

**Example**

If the array is`[1, 2, 3, 3, 4, 5, 10]`, for given target`3`, return`2`.

[**Challenge**](http://lintcode.com/en/problem/first-position-of-target/#challenge)

If the count of numbers is bigger than 2^32, can your code work properly?

```java
class Solution {
    /**
     * @param nums: The integer array.
     * @param target: Target to find.
     * @return: The first position of target. Position starts from 0.
     */
    public int binarySearch(int[] nums, int target) {
       int result = -1;
       
       if (nums == null || nums.length < 1) {
           return -1;
       }
       
       int start = 0;
       int end = nums.length - 1;
       
       while (start <= end) {
           int mid = start + ((end - start)/2);
           if (nums[mid] == target) {
               result = mid;
               end = mid - 1;
           } else if (nums[mid] > target) {
               end = mid - 1;
           } else {
               start = mid + 1;
           }
       }
       
       
       return result;
    }
}
```



