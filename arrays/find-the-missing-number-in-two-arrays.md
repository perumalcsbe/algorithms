Let A,B be two Arrays. Suppose B is a sub-array of A and there is one element that appears only in A.

Find the element of A that is missing in B.

Example:

A = 1, 5, 6, 3, 4, 2

B = 6, 3, 5, 1, 4

Output: 2



```
Approaches
x: Two loops O(N^2)
1. XOR:  all elements from both arrays
2. SUM-SUBTRACT: get SUM of both arrays and subtract
3. HashMap/HashSet:  store B elements in HashMap and then traverse A, check if element not present in HashMap
```



