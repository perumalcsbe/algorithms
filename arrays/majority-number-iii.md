Given an array of integers and a number k, the majority number is the number that occurs`more than 1/k`of the size of the array.

Find it.

##### Notice

There is only one majority number in the array.

**Example**

Given`[3,1,2,3,2,3,3,4,4,4]`and`k=3`, return`3`.

**Approach: HashMap O\(n\) & space O\(1\)**

```java
public class Solution {
    /*
     * @param nums: A list of integers
     * @param k: An integer
     * @return: The majority number
     */
    public int majorityNumber(List<Integer> nums, int k) {
        // base case 
        if (nums == null || k < 1 || nums.size() < 1) return -1;
        
        int n = nums.size();
        int majorityLimit = n/k;
        int num;
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < n; i++) {
            num = nums.get(i);
            int x = map.getOrDefault(num, 0);
            map.put(num, ++x);
            
            if (map.get(num) > majorityLimit) {
                return num;
            }
        }
        
        return -1;
    }
}
```



