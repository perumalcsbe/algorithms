#### Search for a Range

Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order ofO\(logn\).

If the target is not found in the array, return`[-1, -1]`.

For example,  
_`Given[5, 7, 7, 8, 8, 10] and target value 8, return[3, 4].`_

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
function searchRange(nums, target) {
    
    
   const binarySearch = (isFirst = false) => {
      let left = 0;
      let right = nums.length; 
      let lastOccurrence = Number.MIN_VALUE; // -1;
      let firstOccurrence = Number.MAX_VALUE; // arr.length;

      while(left <= right) {  
        // Find middle index
        let mid = left + ((right - left) >>> 1);

        if (nums[mid] === target) {
            if (isFirst) {
                firstOccurrence = Math.min(firstOccurrence, mid);
                right = mid - 1;
            } else {
                lastOccurrence = Math.max(lastOccurrence, mid);
                left = mid + 1;
            }
          
        } else if (nums[mid] < target) { 
          left = mid + 1;
        } else {
          right = mid - 1; 
        }
      }
       
      if (isFirst && firstOccurrence < Number.MAX_VALUE) {
        return firstOccurence;
      }

      if (!isFirst && lastOccurrence > Number.MIN_VALUE) {
        return lastOccurence;
      }
      // not found
      return -1;
    };
    
    let firstIndex = binarySearch(true);
    let lastIndex = binarySearch()
    return [
        firstIndex,
        lastIndex === -1 ? firstIndex : lastIndex
    ];
    
}
```



