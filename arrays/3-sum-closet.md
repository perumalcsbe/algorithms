Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target.  
Return the sum of the three integers.

_Assume that there will only be one solution_

**Example:**  
given array`S = {-1 2 1 -4}`,  
and`target = 1`.

The sum that is closest to the target is`2`.`(-1 + 2 + 1 = 2)`

**Approach: Two Pointers**

```java
public class Solution {
    public int threeSumClosest(ArrayList<Integer> A, int B) {
        
        Collections.sort(A);
        

        int k = A.size()-1;
        int min = Integer.MAX_VALUE;
        int res = 0;
        for (int i = 0; i < A.size()-2; i++) {
            int j = i+1;
        
           while (j < k) {
                int sum = A.get(i) + A.get(j) + A.get(k);
                int diff = Math.abs(B-sum);
                if (diff == 0) {
                    return sum;
                } 
                
                if (diff < min) {
                    min = diff;
                    res = sum;
                } 
                
                if (sum <= B) {
                    j++;
                } else {
                    k--;
                }
                
            }
        
        }
        
        return res;
    }
}

```



