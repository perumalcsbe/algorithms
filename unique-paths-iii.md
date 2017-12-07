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
| x                   | √                     |√
|                     |                       |
v                     v             √         v
up(2,0,3)----------->up(2,1,2)-------------->up(2,2,4)-->x
|                     |                       |
v                     v                       v
x                     x                       x 

```



