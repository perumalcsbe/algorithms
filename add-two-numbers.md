You are given two**non-empty**linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Input:**\(2 -&gt; 4 -&gt; 3\) + \(5 -&gt; 6 -&gt; 4\)  
**Output:**7 -&gt; 0 -&gt; 8

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
    let resultNode = null;
    let temp = null;
    let prev = null;

    let carry = 0;
    while(l1 || l2) {
        let sum = (l1 ? l1.val : 0) + (l2 ? l2.val : 0) + carry;
        carry = sum > 9 ? 1 : 0;
        temp = new ListNode(sum %  10);
        if (!resultNode) {
            resultNode = temp;
        } else {
            prev.next = temp;
        }

        prev = temp;
        if (l1) {
            l1 = l1.next;
        }
        if (l2) {
            l2 = l2.next;
        }
    }
    // if carry is 1 then insert new node with carry
    if (carry) {
        temp = new ListNode(carry);
        prev.next = temp;
    }

    return resultNode;
};
```



