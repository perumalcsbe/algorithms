You are given two **non-empty **linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Follow up:**  
What if you cannot modify the input lists? In other words, reversing the lists is not allowed.

**Example:**

```
Input:(7 ->2 ->4 ->3) + (5 ->6 ->4)

Output:7 ->8 ->0 ->7
```

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
    let stack1 = []; // l1 values
    let stack2 = []; // l2 values
    let stack = []; // l1 + l2 sum
    let result = null; // final linked list
    let temp = null;
    let prev = null;
    let carry = 0;
    // push l1 values to stack1
    while(l1) {
        stack1.push(l1.val);
        l1 = l1.next;
    }
    
    // push l2 values to stack2
    while(l2) {
        stack2.push(l2.val);
        l2 = l2.next;
    }
    
    // pop values from stack1 & stack2 and sum it and push to sum stack
    while(stack1.length || stack2.length) {
        let top1 = stack1.pop() || 0;
        let top2 = stack2.pop() || 0;
        let sum = carry + top1 + top2;
        carry = sum > 9 ? 1 : 0;
        stack.push(sum % 10);
    }
    
    // incase if there is carry then push it sum stack
    if (carry) {
        stack.push(carry);
    }
    
    // pop sum stack and add to result linked list
    while(stack.length) {
        temp = new ListNode(stack.pop());
        if (!result) {
            result = temp;
        } else {
            prev.next = temp;
        }
        
        prev = temp;
        temp = temp.next;
    }
    
    return result;
};
```



