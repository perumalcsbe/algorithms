Given an array of numbers`nums`, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.

For example:

Given`nums = [1, 2, 1, 3, 2, 5]`, return`[3, 5]`.

**Note**:

1. The order of the result is not important. So in the above example,`[5, 3]`is also correct.
2. Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?

##### Approach: Hash Table \(Map\)

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var singleNumber = function(nums) {
    let map = new Map();
    let result = [];
    for (let i = 0; i < nums.length; i++) {
        let count = map.get(nums[i]) || 0;
        map.set(nums[i], ++count);
    }

    for (let [key, value] of map.entries()) {
        if (value < 2) {
            result.push(key);
        }
    }

    return result;
};
```



