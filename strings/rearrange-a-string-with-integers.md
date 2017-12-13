Given a string containing uppercase alphabets and integer digits \(from`0`to`9`\), write a function to return the alphabets in the order followed by the sum of digits.

**Example**

Given str =`AC2BEW3`, return`ABCEW5`  
Alphabets in the lexicographic order, followed by the sum of integers\(2 and 3\).

[**Tags**](http://lintcode.com/en/problem/rearrange-a-string-with-integers/#tags)

[Facebook](http://lintcode.com/tag/facebook/)

```
AC2BEW3
int sum = 0
 0 -> A (prev) A
 1 -> C (cur)  AC      cur < prev ? swap(cur, prev) : continue & prev = cur
 2 -> 2 (cur)  AC      isDigit(cur) ? sum += cur
 3 -> B (cur)  ABC     cur < prev ? swap(cur, prev) && prev = cur
 4 -> E (cur)  ABCE    cur < prev ? swap(cur, prev) && prev = cur
 5 -> W (cur)  ABCEW   cur < prev ? swap(cur, prev) && prev = cur
 6 -> 3 (cur)  ABCEW   isDigit(cur) ? sum += cur
 
 finally return str + sum;
 
```



