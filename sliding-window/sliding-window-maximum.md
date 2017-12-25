Given an array of n integer with duplicate number, and a moving window\(size k\), move the window at each iteration from the start of the array, find the maximum number inside the window at each moving.

**Example**

For array`[1, 2, 7, 7, 8]`, moving window size`k = 3`. return`[7, 7, 8]`

At first the window is at the start of the array like this

`[|1, 2, 7| ,7, 8]`, return the maximum`7`;

then the window move one step forward.

`[1, |2, 7 ,7|, 8]`, return the maximum`7`;

then the window move one step forward again.

`[1, 2, |7, 7, 8|]`, return the maximum`8`;

[**Challenge**](http://lintcode.com/en/problem/sliding-window-maximum/#challenge)

o\(n\) time and O\(k\) memory

```java
public class Solution {
    /*
     * @param nums: A list of integers
     * @param k: An integer
     * @return: The maximum number inside the window at each moving
     */
    public ArrayList<Integer> maxSlidingWindow(int[] nums, int k) {
        ArrayList<Integer> result = new ArrayList<Integer>();

        if (nums == null || nums.length < 1 || nums.length < k) {
            return result;
        }

        // Use Queue for storing k indices 
        LinkedList<Integer> q = new LinkedList<Integer>();

        // traverse an array from 0..n-1
        int i = 0;
        while (i < nums.length) {
            // if Queue has reached k limit then remove head
            if (!q.isEmpty() && q.peek() == i-k) {
                q.poll(); // remove head
            }

            // To keep Queue max value in head always check head with current element and remove
            while (!q.isEmpty() && nums[q.peekLast()] < nums[i]) {
                q.removeLast(); // removes head
            }

            q.offer(i); // safer that q.add(i)

            // for every kth window add Queue head to result
            if (i+1 >= k) {
                result.add(nums[q.peek()]);
            }

            i++;
        }

        return result;
    }
};
```

```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        // base case
        if (nums == null || nums.length < 1 || nums.length < k) {
            return new int[0];
        }
        // use Queue for storing indecies 
        LinkedList<Integer> queue = new LinkedList<>();
        int[] result = new int[nums.length-k+1];
        int j = 0;
        for (int i = 0; i < nums.length; i++) {
            // if queue reached window size then remove head
            if (!queue.isEmpty() && queue.peek() == i-k) {
                queue.poll();
            }
            // To keep Queue max value in head always check head with current element and remove
            while (!queue.isEmpty() && nums[queue.peekLast()] < nums[i]) {
                queue.removeLast();
            }
            
            queue.offer(i);
            
            // add maximum to result
            if (i+1 >= k) {
                result[j++] = nums[queue.peek()];
            }
        }
        
        
        return result;
    }
}
```



