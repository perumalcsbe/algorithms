Given an array with_n_objects colored_red_,_white_or_blue_, sort them so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers`0`,`1`, and`2`to represent the color red, white, and blue respectively.

##### Notice

You are not suppose to use the library's sort function for this problem.  
You should do it in-place \(sort numbers in the original array\).

**Example**

Given`[1, 0, 1, 2]`, sort it in-place to`[0, 1, 1, 2]`.

**Approach: Count Array**

* Traverse array
  * count 0s, 1s & 2s 
* run a loop from 0 to counts
  * assign array indices  with corresponding counts 0, 1, & 2 



[**Challenge**](http://www.lintcode.com/en/problem/sort-colors/#challenge)

A rather straight forward solution is a two-pass algorithm using counting sort.  
First, iterate the array counting number of 0's, 1's, and 2's, then overwrite array with total number of 0's, then 1's and followed by 2's.

Could you come up with an one-pass algorithm using only constant space?

**Approach: Two Pointers**

* assign two points, red = 0, blue as end of array
* begin loop from 0 to end of array
  * if A\[i\] == 0 then move it to end of array
  * if A\[i\] == 2 then move it to blue pointer
  * else move on // A\[i\] == 1

```java
public class Solution {
    /*
     * @param nums: A list of integer which is 0, 1 or 2 
     * @return: nothing
     */
    public void sortColors(int[] nums) {
        if (nums == null || nums.length < 2) return;
        
        int red = 0;
        int blue = nums.length - 1;
        int i = 0;
        while (i <= blue) {
            if (nums[i] == 0) {
                swap(nums, i, red);
                red++;
                i++; // increment i
            } else if (nums[i] == 2) {
                swap(nums, i, blue);
                blue--;
            } else {
                i++;
            }
        }
    }
    
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```



