Given a singly linked list, find middle of the linked list. For example, if given linked list is 1-&gt;2-&gt;3-&gt;4-&gt;5 then output should be 3.

If there are even nodes, then there would be two middle nodes, we need to print second middle element. For example, if given linked list is 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;6 then output should be 4.

```js
//List Node

class ListNode {
  constructor(val) {
     this.val = val;
    this.next = null;
  }
}
```

Approach 1:  Traverse twice

```js
/**
 * @param {head} ListNode
 * return {middle} ListNode 
function findMiddle(head) {
  // traverse LL and find total nodes
  let count = 0;
  let curNode = head;
  while(curNode) {
    count++;
    curNode = curNode.next;
  }
  // reset curNode
  curNode = head;
  let mid = Math.floor(count / 2);
  while(mid > 0 ) {
    mid--;
    curNode = curNode.next;
  }

  return curNode; 
}
```

Approach 2:  Two Pointer

```js
/**
 * @param {head} ListNode
 * return {middle} ListNode 
function findMiddle(head) {
  // slow & past pointers
  let slow = head;
  let past = head;
  while(past && past.next) {
    slow = slow.next;
    // past pointer jumps two nodes
    past = past.next.next;
  }

  return slow; 
}
```



