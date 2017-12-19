Given an array of integers that is already _sorted in ascending order_, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers \(both index1 and index2\) are not zero-based.

##### Notice

You may assume that each input would have exactly one solution.

**Example**

Given nums =`[2, 7, 11, 15]`, target =`9`  
return`[1, 2]`

**Approach: Brute force O\(N^2\)**

```java
public class Solution {
    /*
     * @param nums: an array of Integer
     * @param target: target = nums[index1] + nums[index2]
     * @return: [index1 + 1, index2 + 1] (index1 < index2)
     */
    public int[] twoSum(int[] nums, int target) {
        int[] result = new int[2];
        int i = 0;
        while( i < nums.length - 1) {
            int j = i + 1;
            while(j < nums.length) {
            if (nums[i] + nums[j] == target) {
                result[0] = i + 1;
                result[1] = j + 1;

                return result;

            }
            j++;
            }
            i++;
        }


        return result;
    }
}
```

**Approach: Two Pointers**

```java
public class Solution {
    /*
     * @param nums: an array of Integer
     * @param target: target = nums[index1] + nums[index2]
     * @return: [index1 + 1, index2 + 1] (index1 < index2)
     */
    public int[] twoSum(int[] nums, int target) {
        int[] result = new int[2];
        int start = 0;
        int end = nums.length - 1;
        while(start < end) {
            int sum = nums[start] + nums[end];
            if (sum == target) {
                result[0] = start + 1;
                result[1] = end + 1;

                return result;
            } else if (sum > target) {
                end--;
            } else {
                start++;
            }
        }


        return result;
    }
}
```



