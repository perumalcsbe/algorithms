Given an array _S of n integers, are there elements a_,_b_,c in S such that`a + b + c = 0`? Find all unique triplets in the array which gives the sum of zero.

##### Notice

Elements in a triplet \(a,b,c\) must be in non-descending order. \(ie, a ≤ b ≤ c\)

The solution set must not contain duplicate triplets.

**Example**

For example, given array S =`{-1 0 1 2 -1 -4}`, A solution set is:

```
(-1, 0, 1)
(-1, -1, 2)
```

**Approach: Brute Force**

```
Time Complexity: O(n^3)
Space Complexity: O(1)
```

```java
public class Solution {
    /*
     * @param numbers: Give an array numbers of n integer
     * @return: Find all unique triplets in the array which gives the sum of zero.
     */
    public List<List<Integer>> threeSum(int[] numbers) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        List<Integer> item = new ArrayList<Integer>();

        // base case
        if (numbers == null || numbers.length < 3) {
            return result;
        }

        // sort numbers
        Arrays.sort(numbers);
        //{-4 -1 -1 0 1 2}
        for (int i = 0; i < numbers.length-2; i++) {
            for (int j = i+1; j < numbers.length-1; j++) {
                for (int k = j+1; k < numbers.length; k++) {
                    if (numbers[i] + numbers[j] + numbers[k] == 0) {
                        result.add(Arrays.asList(numbers[i], numbers[j], numbers[k]));
                    }
                }    
            }
        }

        return result;   
    }
}
```

**Approach: Sorting O\(N^2\)**

```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result = new LinkedList<>();
        
        for (int i = 0; i < nums.length-2; i++) {
            if (i == 0 || i > 0 && nums[i] != nums[i-1]) {
                int j = i+1;
                int k = nums.length-1;
                int sum = 0-nums[i];
                while(j < k) {
                    if (nums[j]+nums[k] == sum) {
                        result.add(Arrays.asList(nums[i], nums[j], nums[k]));
                        // for duplicates
                        while(j < k && nums[j] == nums[j+1]) j++;
                        while(j < k && nums[k] == nums[k-1]) k--;
                        j++; 
                        k--;
                    } else if (nums[j]+nums[k] > sum) {
                        k--;
                    } else {
                        j++;
                    }
                }
                
            }
        }
        
        return result;
    }
}
```



