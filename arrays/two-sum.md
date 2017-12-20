Given an array of integers, find two numbers such that they add up to a specific target number.

The function`twoSum`should return \_indices \_of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers \(both index1 and index2\) are **NOT **zero-based.

##### Notice

You may assume that each input would have exactly one solution

##### Approach: HashMap

* traverse array
* for each element, calculate difference of target & current element 
  * store difference as key and index + 1 as value
    * Note: check difference already exists
  * if current element is found in HashMap then return
    * value as first index 
    * current index + 1 as second index

```java
public class Solution {
    /*
     * @param numbers: An array of Integer
     * @param target: target = numbers[index1] + numbers[index2]
     * @return: [index1 + 1, index2 + 1] (index1 < index2)
     */
    public int[] twoSum(int[] numbers, int target) {
        int[] result = new int[2];
        Map<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < numbers.length; i++) {
            int num = numbers[i];
            if (map.containsKey(num)) {
                result[0] = map.get(num);
                result[1] = i + 1;
                break;
            }

            int diff = target - num;
            if (!map.containsKey(diff)) {
                map.put(diff, i + 1);
            }
        }

        return result;
    }
}
```

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] result = new int[2];
        Map<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {
            int num = nums[i];
            if (map.containsKey(target-num)) {
                result[0] = i > map.get(target-num) ? map.get(target-num) : i;
                result[1] = i < map.get(target-num) ? map.get(target-num) : i;
                return result;
            } else {
                map.put(num, i);
            }
        }
        
        return result;
    }
}
```

**Approach : Two Pointers**

