 Given a collection of intervals, merge all overlapping intervals.

**Example**

Given intervals =&gt; merged intervals:

```
[                     [
  [1, 3],               [1, 6],
  [2, 6],      =
>
       [8, 10],
  [8, 10],              [15, 18]
  [15, 18]            ]
]

```

[**Challenge**](http://www.lintcode.com/en/problem/merge-intervals/#challenge)

O\(_n_log_n_\) time and O\(1\) extra space.

```java
/**
 * Definition of Interval:
 * public class Interval {
 *     int start, end;
 *     Interval(int start, int end) {
 *         this.start = start;
 *         this.end = end;
 *     }
 */


public class Solution {
    /*
     * @param intervals: interval list.
     * @return: A new interval list.
     */
    public List<Interval> merge(List<Interval> intervals) {
        List<Interval> result = new ArrayList<Interval>();
        if (intervals.size() < 1) {
            return result;
        }
        
        Collections.sort(intervals, new Comparator<Interval>() {
            @Override
            public int compare(Interval o1, Interval o2) {
                if (o1.start > o2.start)
                    return 1;
                else if (o1.start < o2.start)
                    return -1;
                else {
                    if (o1.end > o2.end)
                        return 1;
                    else if (o1.end < o2.end)
                        return -1;
                }
                return 0;
            }
        });
        
        Interval t = null;
        for (Interval interval : intervals) {
            if (t == null) {
                t = interval;
            } else {
                if (t.end >= interval.start) {
                    t.end = Math.max(t.end, interval.end);
                } else {
                    result.add(t);
                    t = interval;
                }
            }
        }
        
        result.add(t);
        
        return result;
    }
}
```



