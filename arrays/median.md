Given a unsorted array with integers, find the median of it.

A median is the middle number of the array after it is sorted.

If there are even numbers in the array, return the`N/2`-th number after sorted.

**Example**

Given`[4, 5, 1, 2, 3]`, return`3`.

Given`[7, 9, 4, 5]`, return`5`.

[**Challenge**](http://lintcode.com/en/problem/median/#challenge)

O\(n\) time.

**Approach: Naive**

```
Time Complexity: O(nlogn)
```

```java
public class Solution {
    /*
     * @param : A list of integers
     * @return: An integer denotes the middle number of the array
     */
    public int median(int[] nums) {
        Arrays.sort(nums);
        int len = nums.length-1;

        return nums[len/2];
    }
}
```



