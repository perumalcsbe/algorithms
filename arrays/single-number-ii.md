Given an array of integers, every element appears **three** times except for **one**, which appears exactly once. Find that single one.

**Note:**  
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

##### Approach: Hash Table \(Map\)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    let map = new Map();
    for (let i = 0; i < nums.length; i++) {
        let count = map.get(nums[i]) || 0;
        map.set(nums[i], ++count);
    }

    for (let [key, value] of map.entries()) {
        if (value < 3) {
            return key;
        }
    }

    return -1;
};
```



