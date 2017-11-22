### Intersection of Two Arrays II

Given two arrays, write a function to compute their intersection.

**Example:**  
Givennums1=`[1, 2, 2, 1]`,nums2=`[2, 2]`, return`[2, 2]`.

**Note:**

* Each element in the result should appear as many times as it shows in both arrays.
* The result can be in any order.

**Follow up:**

* What if the given array is already sorted? How would you optimize your algorithm?
* What if nums1's size is small compared to nums2's size? Which algorithm is better?
* What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

##### Approach 1: Using Map

```js
function intersection(nums1, nums2) {
    let map = new Map();
    let result = [];
    
    for (let n of nums1) {
        let count = map.get(n) || 0;
        map.set(n, ++count);
    }
    
    for (let n of nums2) {
        if (map.has(n)) {
            // delete mapped values
            if (map.get(n) > 1) {
                map.set(n, map.get(n) - 1);
            } else {
                map.delete(n);
            }
            result.push(n);
        }
    }
    
    return result;
}
```



