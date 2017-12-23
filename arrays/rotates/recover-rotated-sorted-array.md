Given a **rotated **sorted array, recover it to sorted array in-place.

**Clarification**

What is rotated array?

* For example, the orginal array is \[1,2,3,4\], The rotated array of it can be \[1,2,3,4\], \[2,3,4,1\], \[3,4,1,2\], \[4,1,2,3\]

**Example**

`[4, 5, 1, 2, 3]`-&gt;`[1, 2, 3, 4, 5]`

[**Challenge**](http://www.lintcode.com/en/problem/recover-rotated-sorted-array/#challenge)

In-place, O\(_1_\) extra space and O\(_n_\) time.

**Approach: Naive**

```java
public class Solution {
    /*
     * @param nums: An integer array
     * @return: nothing
     */
    public void recoverRotatedSortedArray(List<Integer> nums) {
        // base case
        if (nums.size() < 2 || nums.get(0) < nums.get(nums.size()-1)) {
            return;
        }
        
        int k = 0; 
        while (k < nums.size()-1) {
            if (nums.get(k) > nums.get(k+1)) {
                break;
            }
            k++;
        }
        
        
       
        for (int i = 0; i < k+1; i++) {
            for (int j = 0; j < nums.size()-1; j++) {
                int temp = nums.get(j);
                nums.set(j, nums.get(j+1));
                nums.set(j+1, temp);
            }
        }
    }
}
```



