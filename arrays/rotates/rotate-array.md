Rotate an array ofnelements to the right by **k** steps.

For example, with n= 7 and k= 3, the array`[1,2,3,4,5,6,7]`is rotated to`[5,6,7,1,2,3,4]`.

**Note: **Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.

**Hint: **Could you do it in-place with O\(1\) extra space?

**Approach:  ArrayCopy**

```
A [1,2,3,4,5,6,7] k = 3
1. create new array B
2. add 3 elements from end
3. add n-3 elements from begining
4. modify original array
// System.arraycopy(A, 0, B, 0, n);
Time Complexity: O(n) Space Complexity: O(n)
```

```java
class Solution {
    public void rotate(int[] nums, int k) {
        // base case
        if (k == 0 || nums.length < 2) {
            return;
        }

        // case where k > nums length
        if (k > nums.length) {
            k = k%nums.length;
        }
        int n = nums.length;
        int[] temp = new int[n];

        for (int i = 0; i < k; i++) {
            temp[i] = nums[n-k+i];
        }
        int j = 0;
        for (int i = k; i < n; i++) {
            temp[i] = nums[j];
            j++;
        }

        System.arraycopy(temp, 0, nums, 0, n);
    }
}
```

**Approach:  Bubble Sort**

```
A [1,2,3,4,5,6,7] k = 3
1. Run outer loop of k times
2. Traverse from end of A and move larger to first
e.g. 
 step1: [7,1,2,3,4,5,6]
 step2: [6,7,1,2,3,4,5]
 step3: [5,6,7,1,2,3,4]

Time Complexity: O(k*n) Space Complexity: O(1)
```

```java
class Solution {
    public void rotate(int[] nums, int k) {
        // base case
        if (k == 0 || nums.length < 2) {
            return;
        }
        int n = nums.length;

        // case where k > nums length
        if (k > n) {
            k = k%n;
        }


        for (int i = 0; i < k; i++) {
            for (int j = nums.length-1; j > 0; j--) {
                int temp = nums[j];
                nums[j] = nums[j-1];
                nums[j-1] = temp;
            }
        }
    }
}
```

**Approach: Reverse**

```
A [1,2,3,4,5,6,7] k = 3
1. reverse A from 0 to n-k
2. reverse A n-k to n-1
3. reverse A

e.g. 
 step1: [4,3,2,1,5,6,7]
 step2: [4,3,2,1,7,6,5]
 step3: [5,6,7,1,2,3,4]


```



