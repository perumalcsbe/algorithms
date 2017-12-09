Follow up for "Unique Paths II":[http://lintcode.com/en/problem/unique-paths-ii/](http://lintcode.com/en/problem/unique-paths-ii/)

```
A robot is located at the top-left corner of a_m_x_n_grid.
The robot can only move either down or right at any point in time. 
The robot is trying to reach the bottom-right corner of the grid.
```

Now each grid contains a value, so each path also has a value. Find the`sum`of all the`unique values`paths.

**Example**

For example,

```
[
  [1,1,2],
  [1,2,3],
  [3,2,4]
]
```

There are 2 unique value path:  
`[1,1,2,3,4] = 11`  
`[1,1,2,2,4] = 10`

return`21`

```
             √                      √
up(0,0,1)----------->up(0,1,1)-------------->up(0,2,2)-->x
|                     |                       |
|√                    |√                      | √
|                     |                       |
v            √        v            x          v
up(1,0,1)----------->up(1,1,2)-------------->up(1,2,3)-->x 
|                     |                       |
| √                   | √                     |√
|                     |                       |
v            √        v             √         v
up(2,0,3)----------->up(2,1,2)-------------->up(2,2,4)-->x
|                     |                       |
v                     v                       v
x                     x                       x
```

**Top Down Approach**

* breakdown moves \(left & right\), calculate their sum
* For every _**k**\_th node, _**i** & **j** represents row & column then, calculating path is **k\(i\)**\_th value + any one of the below
* * if left **k\(i, j + 1\)** == bottom _**k\(i+1, j\)**_ then take either left**k\(i, j + 1\)** or right value
  * if left**k\(i, j + 1\)** != bottom _**k\(i+1, j**_ then take both values
  * if no left **k\(i, j + 1\)** and has bottom then take bottom _**k\(i+1, j\)**_
  * if no bottom_**k\(i+1, j\)**_ and has left then take left**k\(i, j + 1\)**
  * if no left **k\(i, j + 1\)** & bottom _**k\(i+1, j\)**_ then **0**

```
[
    [1,1,2],
    [1,2,3],
    [3,2,4]
]
```

| mxn | 0 | 1 | 2 |
| :--- | :--- | :--- | :--- |
| 0 | 1 | 2 \(1+1\) | 4\(2+2\) |
| 1 | 2\(1+1\) | 4 \( 2 + 2\) t==l | 7\(3+4\) t==l |
| 2 | 5\(2+3\) | 10 \(2+ 4 +5 -1\) t!=l | 21\(4+7+10\) t!=l |



