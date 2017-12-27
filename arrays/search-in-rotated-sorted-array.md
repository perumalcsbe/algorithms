Suppose a sorted array is rotated at some pivot unknown to you beforehand.

\(i.e.,`0 1 2 4 5 6 7`might become`4 5 6 7 0 1 2`\).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

**Example**

For`[4, 5, 1, 2, 3]`and`target=1`, return`2`.

For`[4, 5, 1, 2, 3]`and`target=0`, return`-1`.

[**Challenge**](http://www.lintcode.com/en/problem/search-in-rotated-sorted-array/#challenge)

O\(logN\) time

```
public class Solution {
	// DO NOT MODIFY THE LIST
	public int search(final List<Integer> a, int b) {
	    int start = 0;
	    int end = a.size()-1;
	    
	    while (start <= end) {
	        int mid = start + (end - start)/2;
	        // if mid is target then return
	        if (a.get(mid) == b) {
	            return mid;
	        } 
	        
	        // if mid is greater than start
	        if (a.get(start) <= a.get(mid)) {
	            
	            if (a.get(start) <= b && b < a.get(mid)) {
	                end = mid-1;
	            } else {
	                start = mid+1;
	            }
	        } else {
	            if (a.get(mid) < b && b <= a.get(end)) {
	                start = mid+1;
	            } else {
	                end = mid-1;
	            }
	        }
	    }
	    
	    return -1;
	}
}

```



