Find the**k**th largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

For example,  
Given`[3,2,1,5,6,4]`and k = 2, return 5.

**Note:**  
You may assume k is always valid, 1 ≤ k ≤ array's length.

```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        if (nums == null || nums.length < 1 || k < 1) {
            return -1;
        }
        PriorityQueue<Integer> pq = new PriorityQueue(k, new Comparator<Integer>() {
            public int compare(Integer c1, Integer c2) {
                return c2 - c1;
            }
        });

            for (int i = 0; i < nums.length; i++) {
                pq.offer(nums[i]);
            }
            for (int j = 0; j < k - 1; j++) {
                pq.poll();
            }

            return pq.peek();
    }
}
```



