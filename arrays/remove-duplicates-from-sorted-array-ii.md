Follow up for "Remove Duplicates":  
What if duplicates are allowed at most twice?

For example,  
Given sorted array A = `[1,1,1,2,2,3]`,

Your function should return length = `5`, and A is now `[1,1,2,2,3]`.

**Approach: Two Pointers**

```java
public class Solution {
    /**
     * @param A: a array of integers
     * @return : return an integer
     */
    public int removeDuplicates(int[] nums) {
        if (nums.length <= 2) {
            return nums.length;
        }
        int prev = 1;
        int cur = 2;
        while (cur < nums.length) {

            if (nums[prev] == nums[cur] && nums[prev-1] == nums[cur]) {
               cur++;
            } else {
                prev++;
                nums[prev] = nums[cur];
                cur++;
            }
       }

       return prev+1;
    }
}
```



