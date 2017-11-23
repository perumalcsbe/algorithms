Given an array of integers, every element appears **twice** except for **one**. Find that single one.

**Note:**  
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

##### Approach 1: Brute Force \| Naive Method

* first sort array O\(logn\) so that, each repeating element appears next each other
* run a loop, 
  * take current element and check with next element if not matched then return current element 

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
      nums.sort((a, b) => a - b);
      for (let i = 0; i < nums.length; i++) {
            if (nums[i] !== nums[i + 1]) {
                  return nums[i];
            } else {
                  i++; 
            }
      }

      return -1;
};
```

##### Approach 2: Hash Table \(Map\)

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
            if (value < 2) {
                  return key;
            }
      }

      return -1;
};
```

##### 

##### Approach 2: XOR

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
      let result = 0;
      for (let i = 0; i < nums.length; i++) {
            result ^= nums[i];
      }

      return result;
};
```



