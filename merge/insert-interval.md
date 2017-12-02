Given a non-overlapping interval list which is sorted by start point.

Insert a new interval into it, make sure the list is still in order and**non-overlapping**\(merge intervals if necessary\).

**Example**

Insert**\[2, 5\]**into**\[\[1,2\], \[5,9\]\]**, we get**\[\[1,9\]\]**.

Insert**\[3, 4\]**into**\[\[1,2\], \[5,9\]\]**, we get**\[\[1,2\], \[3,4\], \[5,9\]\]**.

```java

/**
 * Definition of Interval:
 * public classs Interval {
 *     int start, end;
 *     Interval(int start, int end) {
 *         this.start = start;
 *         this.end = end;
 *     }
 */


public class Solution {
    /*
     * @param intervals: Sorted interval list.
     * @param newInterval: new interval.
     * @return: A new interval list.
     */
    public List<Interval> insert(List<Interval> intervals, Interval newInterval) {
        List<Interval> result = new ArrayList<Interval>();
        if (intervals.size() < 1) {
            result.add(newInterval);
            return result;
        }
        
        intervals.add(newInterval);
        
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



