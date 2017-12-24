There are two sorted arrays **nums1 **and **nums2 **of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O\(log \(m+n\)\).

**Example 1:**

```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```

**Example 2:**

```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

```
if total length is odd then value of middle index is median
if total length is even then value of middle + next index / 2 is median
traverse both array.. as soon as middle index found return it
```



