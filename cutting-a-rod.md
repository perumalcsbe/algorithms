Given a rod of length`n`inches and an array of prices that contains prices of all pieces of size smaller than`n`. Determine the maximum value obtainable by cutting up the rod and selling the pieces. For example, if length of the rod is`8`and the values of different pieces are given as following, then the maximum obtainable value is`22`\(by cutting in two pieces of lengths`2`and`6`\)

**Example**

```
length   | 1   2   3   4   5   6   7   8  
--------------------------------------------
price    | 1   5   8   9  10  17  17  20

```

Given price =`[1, 5, 8, 9, 10, 17, 17, 20]`, n =`8`  
Return`22`// by cutting in two pieces of lengths 2 and 6

```
length   | 1   2   3   4   5   6   7   8  
--------------------------------------------
price    | 3   5   8   9  10  17  17  20

```

Given price =`[3, 5, 8, 9, 10, 17, 17, 20]`, n =`8`  
Return`24`// by cutting in eight pieces of length 1

```
Analysis
length   | 1   2   3   4   5   6   7   8  
--------------------------------------------
       1   8   20  3   4   5   6   7   8
       2   2      
       3   3
       4   4
       5   5
       6   6
       7   7
       8   8
       
price    | 
       1 |  
       5 |
       8 |  
       9 | 
      10 |  
      17 | 
      17 |
      20 |



# subproblems
      consider P as maximum optimized value 
      to get P(n)th piece is depends of P(n-1)th piece, therefore
        P(n) = MAX(P(n-1)

```



