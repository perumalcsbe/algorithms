Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

##### Notice

This problem have two method which is`Greedy`and`Dynamic Programming`.

The time complexity of`Greedy`method is`O(n)`.

The time complexity of`Dynamic`Programming method is`O(n^2)`.

We manually set the small data set to allow you pass the test in both ways. This is just to let you learn how to use this problem in dynamic programming ways. If you finish it in dynamic programming ways, you can try greedy method to make it accept again.

**Example**

A =`[2,3,1,1,4]`, return`true`.

A =`[3,2,1,0,4]`, return`false`.

**Approach: Recursion**

```
Base case: for terminating recursion 
  1 false if current value is 0
  2 false if current value > array length - 1
  3 true if current value == array length - 1

subproblem:
    case 1. current index + A[current index]
    case 2. run loop from previous index to current index and try case 1
```

**Approach: Dynamic Programming**

```
  [0,1,2,3,4] => 4  
A [2,3,1,1,4]
i i + A[i]..i-1 + A[n-1] => true 
0 0 + 2    => 2
2 2 + 1    => 3
3 3 + 1    => 4 √
A [3,2,1,0,4]
Taking max jump
0 0 + 3    => 3
3 3 + 0    => 3 x
Taking min jump
0 0 + 3    => 3
for (int j = A[i]; j > A[i]-i || 0; j--) {
2 2 + 1    => 3
3 3 + 0    => 3 x
-----
1 1 + 2    => 3
3 3 + 0    => 3 x 
}    
   
```



