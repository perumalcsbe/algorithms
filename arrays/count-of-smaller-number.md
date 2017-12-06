Give you an integer array \(index from 0 to n-1, where n is the size of this array, value from 0 to 10000\) and an query list. For each query, give you an integer, return the number of element in the array that are smaller than the given integer.

##### Notice

We suggest you finish problem [Segment Tree Build](http://www.lintcode.com/problem/segment-tree-build/) and [Segment Tree Query II](http://lintcode.com/en/problem/segment-tree-query-ii/)f irst.

**Example**

For array`[1,2,7,8,5]`, and queries`[1,8,5]`, return`[0,4,2]`

[**Challenge**](http://www.lintcode.com/en/problem/count-of-smaller-number/#challenge)

Could you use three ways to do it.

1. Just loop
2. Sort and binary search
3. Build Segment Tree and Search.

**Approach: Loop**

```java
public class Solution {
    /*
     * @param A: An integer array
     * @param queries: The query list
     * @return: The number of element in the array that are smaller that the given integer
     */
    public List<Integer> countOfSmallerNumber(int[] A, int[] queries) {
       List<Integer> result = new ArrayList<>();

       for (int q: queries) {
           int s = 0;
           for (int a: A) {
               if (a < q) {
                   s++;
               }
           }

           result.add(s);
       }

       return result;
    }
}
```

Approach: Binary search

