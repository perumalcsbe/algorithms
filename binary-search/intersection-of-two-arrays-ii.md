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

```java
public class Solution {
    
    /*
     * @param nums1: an integer array
     * @param nums2: an integer array
     * @return: an integer array
     */
    public int[] intersection(int[] nums1, int[] nums2) {
        int[] noRes = new int[0];
        
        if (nums1.length < 1 || nums2.length < 1) return noRes;
        
        Map<Integer, Integer> map = new HashMap<>();
        
        List<Integer> list = new ArrayList<>();
        
        for (int i = 0; i < nums1.length; i++) {
            map.put(nums1[i], 1 + map.getOrDefault(nums1[i], 0));
        }
        
        for (int i = 0; i < nums2.length; i++) {
            if (map.containsKey(nums2[i])) {
                list.add(nums2[i]);
                // delete mapped values
                if (map.get(nums2[i]) > 1) {
                    map.put(nums2[i], map.get(nums2[i]) - 1);
                } else {
                    map.remove(nums2[i]);
                }
            }
        }
        
        int[] result = new int[list.size()];
        for (int i = 0; i < list.size(); i++) {
            result[i] = list.get(i);
        }
        
        return result;
    }
};
```



