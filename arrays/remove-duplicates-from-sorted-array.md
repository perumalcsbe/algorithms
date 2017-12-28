Given a sorted array, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array **[**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) with O\(1\) extra memory.

**Example:**

```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
It doesn't matter what you leave beyond the new length.
```

##### Approach 1: [Two Pointers](/two-pointers.md)

```java
public class Solution {
    /*
     * @param nums: An ineger array
     * @return: An integer
     */
    public int removeDuplicates(int[] nums) {
        if (nums == null || nums.length < 2) {
            return nums.length;
        }
       int k = 0; // 
       int i = 1;

       while (i < nums.length) {

            if (nums[i] == nums[k]) {
               i++;
            } else {
                k++;
                nums[k] = nums[i];    
                i++;
            }
       }

       return k+1;
    }
}
```

**Approach: Slice in JS**

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
function removeDuplicates(nums) {
    let LEN = nums.length;
    if (LEN < 1) return nums;

    for(let i = 0, j = 1; i < j && j < nums.length; j = i + 1) {
        if (nums[i] === nums[j]){
          nums.splice(j, 1);
        } else {
            i++;
        }
    }

    return nums.length;
}
```

**Approach: Unique elements**

this will return unique counts if expectation is only length

```java
public class Solution {
    /*
     * @param nums: An ineger array
     * @return: An integer
     */
    public int removeDuplicates(int[] nums) {
        if (nums == null || nums.length < 2) {
            return nums.length;
        }
       int k = 0;
       int i = 0;

       while (i < nums.length-1) {
            if (nums[i] == nums[i+1]) {
               k++;
            }
            i++;
       }

       return nums.length-k;
    }
}
```



