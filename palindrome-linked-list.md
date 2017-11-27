Given a singly linked list, determine if it is a palindrome.

**Follow up:**  
Could you do it in O\(n\) time and O\(1\) space?

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {boolean}
 */
var isPalindrome = function(head) {
  // if list is empty then return true
   if (!head) return true;
    
  let cur = head; // slow pointer
  let past = head; // past pointer 
  let stack = []; 
    // push values to stack until slow/cur pointer reaches to Middle of the list
  while(past && past.next) {
    stack.push(cur.val); 
    cur = cur.next;
    
    past = past.next.next;
  }
  
  // if past pointer is not null then go to next node
  if (past) cur = cur.next;
  
  // start from Middle node and check with stack elements
  while(cur) {
    if (stack.pop() !== cur.val) return false;
    cur = cur.next;
  }
    
  return true;
};
```



