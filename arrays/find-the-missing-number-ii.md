Giving a string with number from 1-`n`in random order, but miss`1`number.Find that number.

##### Notice

n &lt;= 30

**Example**

Given n =`20`, str =`19201234567891011121314151618`

return`17`



**Approach: BackTracking**

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 9 | 20 | 12 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 18 |  |



