Given an array and a value, remove all instances of that value [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array **[**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) with O\(1\) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

**Example:**

```
Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.
```

##### Approach 1:

```js
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */
function removeElement(nums, val) {
    let i = 0;
    while ( i <= nums.length ) {
        if (val === nums[i]) {
            nums.splice(i, 1); // once element removed then current index is next index 
        } else {
            i++;
        }
    }

    return nums.length;
}
```

##### Approach 2: [Two Pointers](/two-pointers.md)

```js
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */
function removeElement(nums, val) {
    let i = 0;
    let j = nums.length - 1;
    while ( i <= j ) {
        if (val === nums[i]) {
            nums.splice(i, 1); // once element removed then current index is next index 
            j--;
        } else {
            i++;
        }
    }

    return nums.length;
}
```



