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

```java
    /*
     * @param A: An integer array
     * @return: An integer
     */
    public int singleNumberII(int[] A) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < A.length; i++) {
            int count = 1;
            if (map.containsKey(A[i])) {
                count += map.get(A[i]);
            }

            map.put(A[i], count);

        }

        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            if (entry.getValue() < 3) {
                return entry.getKey();
            }
        }

        return -1;
    }
    
```

**Approach: Bit Manipulation**

```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int singleNumber(final List<Integer> A) {
        int ones = 0;
        int twos = 0;
        int threes = 0;
        
        for (int a: A) {
            twos |= ones & a;
            ones ^= a;
            threes = ones & twos;
            twos &= ~threes;
            ones &= ~threes;
        }
        
        return ones;
    }
}

```





