Give an integer array，find the longest increasing continuous subsequence in this array.

An increasing continuous subsequence:

* Can be from right to left or from left to right.
* Indices of the integers in the subsequence should be continuous.

##### Notice

O\(n\) time and O\(1\) extra space.

**Example**

For`[5, 4, 2, 1, 3]`, the LICS is`[5, 4, 2, 1]`, return`4`.

For`[5, 1, 2, 3, 4]`, the LICS is`[1, 2, 3, 4]`, return`4`.

> this is similar to Longest increasing subsequence the ask here is both directions

| index | 0 | 1 | 2 | 3 | 4 | 5 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| left -&gt; right | 1 | 1 | 1 | 1 | 2 | 2 |
| right -&gt; left | 1 | 1 | 2 | 3 | 4 | 4 |

```

```



