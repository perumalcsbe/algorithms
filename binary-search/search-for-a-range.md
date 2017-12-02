#### Search for a Range

Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order ofO\(logn\).

If the target is not found in the array, return`[-1, -1]`.

For example,  
`Given[5, 7, 7, 8, 8, 10] and target value 8, return[3, 4].`

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

```java
public class Solution {
    /*
     * @param A: an integer sorted array
     * @param target: an integer to be inserted
     * @return: a list of length 2, [index1, index2]
     */
    public int[] searchRange(int[] A, int target) {
        int[] result = new int[2];
        
        result[0] = binarySearch(A, 0, A.length - 1, target, true);
        int last = binarySearch(A, 0, A.length - 1, target, false);
        if (last < 0) {
            last = result[0];
        }
        result[1] = last;
        return result;
    }
    
    private int binarySearch(int[] A, int low, int high, int target, boolean isFirst) {
        if (A == null || A.length == 0) {
            return -1;
        }
        int first = Integer.MAX_VALUE;
        int last = Integer.MIN_VALUE;
        
        while (low <= high) {
            int mid = low + (( high - low) >>> 1);
            
            if (A[mid] == target) {
                if (isFirst) {
                    first = Math.min(first, mid);
                    high = mid - 1;
                } else {
                    last = Math.max(last, mid);
                    low = mid + 1;
                }
                
            } else if (A[mid] > target) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
            
        }
        
        if (isFirst && first < Integer.MAX_VALUE) {
            return first;
        } 
        
        if (!isFirst && last > Integer.MIN_VALUE) {
            return last;
        } 

        
        return -1;
    }
}
```



