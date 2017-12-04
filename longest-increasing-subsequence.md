Given a sequence of integers, find the longest increasing subsequence \(LIS\).

You code should return the length of the LIS.

**Clarification**

What's the definition of longest increasing subsequence?

* The longest increasing subsequence problem is to find a subsequence of a given sequence in which the subsequence's elements are in sorted order, lowest to highest, and in which the subsequence is as long as possible. This subsequence is not necessarily contiguous, or unique.

* [https://en.wikipedia.org/wiki/Longest\_increasing\_subsequence](http://www.lintcode.com/en/problem/longest-increasing-subsequence/)

**Example**

For`[5, 4, 1, 2, 3]`, the LIS is`[1, 2, 3]`, return`3`  
For`[4, 2, 4, 5, 3, 7]`, the LIS is`[2, 4, 5, 7]`, return`4`

##### 

**Approach: Recursive O\(2^n\)**

```java
public class Solution {
    /*
     * @param nums: An integer array
     * @return: The length of LIS (longest increasing subsequence)
     */
    public int longestIncreasingSubsequence(int[] nums) {
        // base case
        if (nums == null || nums.length < 1) return 0;

        return longestIncreasingSubsequence(nums, 0, nums.length, Integer.MIN_VALUE);
    }

    private int longestIncreasingSubsequence(int[] nums, int start, int end, int prev) {

        // base case: if start reaches end then stop
        if (start == end) {
            return 0;
        }

        // case 1: exclude integer
        int exclude = longestIncreasingSubsequence(nums, start + 1, end, prev);

        // case 2: include integer
        int include = 0;
        // include if current number greater than prev 
        if (nums[start] > prev) {
            include = 1 + longestIncreasingSubsequence(nums, start + 1, end, nums[start]);
        }

        // finally return the maximum of exclude number and including number
        return Math.max(exclude, include);
    }
}
```

**Approach: Dynamic Programming O\(n^2\) space: O\(n\)**

```js
function LIS(arr) {
  // base case
  if (arr == null || arr.length < 1) return 0;

  const n = arr.length;
  // create array length of given array length for storing subproblem result;
  let lis = Array(n).fill(0);

  lis[0] = 1; // when there is one item in the array 

  // start from second element
  for (let i = 1; i < n; i++) { // arr[1..n]

    for (let j = 0; j < i; j++) { // arr[0...i-1]

      // if current element is greater than prev element
      if (arr[i] > arr[j] && lis[j] > lis[i]) {
        lis[i] = lis[j];
      }

    }
    // include arr[i] in lis
    lis[i]++;
  }

  return Math.max.apply(null, lis);

}
```

```java
public class Solution {
    /*
     * @param nums: An integer array
     * @return: The length of LIS (longest increasing subsequence)
     */
    public int longestIncreasingSubsequence(int[] nums) {
        // base case
        if (nums == null || nums.length < 1) return 0;
        
        int n = nums.length;
        int[] LIS = new int[n];
        
        LIS[0] = 1; // when array length is 1
        
        // start from second elment from array
        for (int i = 1; i < n; i++) {
            
            // start inner loop from 0 to i-1
            for (int j = 0; j < i; j++) {
                // check of current element nums[i] > nums[j] and  
                //LIS[j] < LIS[i] then take LIS[j]  value
                
                if (nums[i] > nums[j] && LIS[j] > LIS[i]) {
                    LIS[i] = LIS[j];
                }
            }
            
            // increament the index value
            LIS[i]++;
        }
        
        
        int lis = Integer.MIN_VALUE;
        
        for (int x: LIS) {
            lis = Math.max(lis, x);
        }
        
        
        return lis;
    }
}
```



