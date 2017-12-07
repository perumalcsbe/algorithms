Given an **unsorted **integer array, find the first **missing **positive integer.

**Example**

Given`[1,2,0]`return`3`,  
and`[3,4,-1,1]`return`2`.

[**Challenge**](http://www.lintcode.com/en/problem/first-missing-positive/#challenge)

Your algorithm should run in O\(_n_\) time and uses constant space.

**Approach:  Boolean Array**

> Example: \[1, 2, 0\] and length = 3 + 1

| index | 0 | 1 | 2 | 3 |
| :--- | :--- | :--- | :--- | :--- |
| value | ~~0~~1 | ~~0~~ 1 | ~~0~~1 | 0 |

> Example \[3,4,-1,1\] and length = 4+1

| index | 0 | 1 | 2 | 3 | 4 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| initial | ~~0~~1 | ~~0~~1 | 0 | ~~0~~1 | ~~0~~1 |



