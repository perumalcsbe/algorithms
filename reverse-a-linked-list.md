Reverse a linked list.

**Example**

For linked list`1->2->3`, the reversed linked list is`3->2->1`

[**Challenge**](http://lintcode.com/en/problem/reverse-linked-list/#challenge)

Reverse it in-place and in one-pass

```
head-->(1)->(2)->(3)->null
        |
temp -> head
Output:– 3->2->1->null
```

```js
function reverseList(head) {
    let temp = null;
    let nextNode = null;

    while(head) {
        nextNode = head.next;
        head.next = temp;
        temp = head;
        head = nextNode;
    }

    return temp;
}
```

```java
/**
 * Definition for ListNode.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int val) {
 *         this.val = val;
 *         this.next = null;
 *     }
 * }
 */


public class Solution {
    /*
     * @param head: n
     * @return: The new head of reversed linked list.
     */
    public ListNode reverse(ListNode head) {
        ListNode temp = null;
        ListNode nextNode = null;
        
        while (head != null) {
            nextNode = head.next;
            head.next = temp;
            temp = head;
            head = nextNode;
        }
        
        return temp;
    }
}
```



