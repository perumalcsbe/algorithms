Partition an integers array into odd number first and even number second.

Given`[1, 2, 3, 4]`, return`[1, 3, 2, 4]`

[**Challenge**](http://www.lintcode.com/en/problem/partition-array-by-odd-and-even/#challenge)

Do it in-place.



```java
public class Solution {
    /*
     * @param nums: an array of integers
     * @return: nothing
     */
    public void partitionArray(int[] nums) {
        if (nums == null) return;
        int i = 0;
        int j = nums.length - 1;
        while(i < j) {
             
             //ODD
            while (i < j && nums[i] % 2 != 0) {
                i++;
            } 
            
            //EVEN
            while (i < j && nums[j] % 2 == 0) {
                    j--;
            }
            
            if (i < j) {
                int t = nums[i];
                nums[i] = nums[j];
                nums[j] = t;
            }
        }
    }
}
```



