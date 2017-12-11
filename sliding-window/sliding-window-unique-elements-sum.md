Given an array and a window size that is sliding along the array, find the sum of the count of unique elements in each window.

**Example**

Given a array nums =`[1, 2, 1, 3, 3]`and`k = 3`

First window`[1, 2, 1]`, only`2`is unique, count is 1.  
Second window`[2, 1, 3]`, all elements unique, count is 3.  
Third window`[1, 3, 3]`, only`1`is unique, count is 1.  
sum of count =`1 + 3 + 1 = 5`

Return`5`

##### Approach: HashMap

![](/assets/slidingwindowunique.png)

* create HashMap to store number and its count
* traverse array from start to end
  * remove number or decrement count for every number after window size
  * add every number and its count to HashMap
  * whenever start about to reach window size then get unique count from hashmap and add it result 
* Special case if window size greater than array size then get unique count from hashmap and add it result

```java
public class Solution {
    /*
     * @param : the given array
     * @param : the window size
     * @return: the sum of the count of unique elements in each window
     */
    public int slidingWindowUniqueElementsSum(int[] nums, int k) {
        if (nums == null || nums.length < 1) {
            return 0;
        }

        int result = 0;
        HashMap<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            // for every window limit k - remove first item 
            if (i >= k) {
                int first = nums[i-k];
                int count = map.get(first);
                if (count > 1) {
                    map.put(first, --count);
                } else {
                    map.remove(first);
                }
            }
            int cur = nums[i];
            int cur_count = map.getOrDefault(cur, 0);
            map.put(cur, ++cur_count);

            // for every kth limit take unique count
            if (i+1 >= k) {
                for (Map.Entry<Integer, Integer> entry: map.entrySet()) {
                    if (entry.getValue() == 1) {
                        result++;
                    }
                }
            }
        }

        // case where k > nums.length

        if (k > nums.length) {
            for (Map.Entry<Integer, Integer> entry: map.entrySet()) {
                    if (entry.getValue() == 1) {
                        result++;
                    }
                }
        }

        return result;
    }
};
```

**Approach: Dynamic Programming**

