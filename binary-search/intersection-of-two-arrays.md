### Intersection of Two Arrays

Given two arrays, write a function to compute their intersection.

**Example:**  
Given **nums1**=\[1, 2, 2, 1\], **nums2**=\[2, 2\], return \[2\].

**Note:**

* Each element in the result must be unique.
* The result can be in any order.

##### Approach 1:  Two loops

```js
function intersection(nums1, nums2) {
    let result = new Set(); // for unique results
    for (let i = 0; i < nums1.length; i++) {
        for (let j = 0; j < nums2.length; j++) {
            if (nums1[i] === nums2[j]) {
                result.add(nums1[i]);
            }
        }
    }

    return Array.from(result);
}
```

```
Run Time Complexity: O(n^2)
Auxiliary Space: O(1)
```

##### Approach 2: Using Set

```js
function intersection(nums1, nums2) {
    let set1 = new Set(Array.from(nums1));
    let result = new Set();
    for(let i = 0; i < nums2.length; i++) {
         if (set1.has(nums2[i])) {
             result.add(nums2[i]);
         }   
    }

    return Array.from(result);
}
```

```
Time Complexity: O(n)
Space Complexity: O(P) where P is Length of any one of the Array
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
         
        Set<Integer> set = new HashSet<>();
        HashSet<Integer> resultSet = new HashSet<>();
        for (int i = 0; i < nums1.length; i++) {
            set.add(nums1[i]);
        }
        
        for (int i = 0; i < nums2.length; i++) {
            if (set.contains(nums2[i])) {
                resultSet.add(nums2[i]);
            }
        }
        int[] result = new int[resultSet.size()];
        int i = 0;
        for (Integer val : resultSet) result[i++] = val;
        return result;
    }
}; 
```



