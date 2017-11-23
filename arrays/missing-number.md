Given an array containing **n** distinct numbers taken from`0, 1, 2, ..., n`, find the one that is missing from the array.

For example,  
Givennums=`[0, 1, 3]`return`2`.

**Note**:  
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?



##### Approach 1: Boolean Array

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var missingNumber = function(nums) {
    let map = Array(nums.length + 1).fill(false);
    for(let v of nums) {
        map[v] = true;
    }
    for (let i = 0; i < map.length; i++) {
        if (!map[i]) {
            return i;
        }
    }
    
    return -1;
}; 
```

```
Time Complexity: O(n)
Space Complexity: O(n)?
```



