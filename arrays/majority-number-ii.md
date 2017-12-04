Given an array of integers, the majority number is the number that occurs`more than 1/3`of the size of the array.

Find it.

##### Notice

There is only one majority number in the array.

**Example**

Given`[1, 2, 1, 2, 1, 3, 3]`, return`1`.



**Approach: HashMap O\(n\) Space Complexity: O\(1\)**

```java
public class Solution {
    /*
     * @param nums: a list of integers
     * @return: The majority number that occurs more than 1/3
     */
    public int majorityNumber(List<Integer> nums) {
        // base case
        if (nums == null || nums.size() < 1) return -1;
        
        int n = nums.size();
        int num;
        int majorityLimit = n / 3;
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < n; i++) {
            num = nums.get(i);
            Integer x = map.getOrDefault(num, 0);
            
            map.put(num, ++x);
            
            if (map.get(num) > majorityLimit) {
                return num;
            }
        }
        
        return -1;
        
    }
}
```



