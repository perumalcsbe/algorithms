Given a sorted linked list, delete all duplicates such that each element appear onlyonce.

For example,  
Given`1->1->2`, return`1->2`.  
Given`1->1->2->3->3`, return`1->2->3`.

![](/assets/duplicate_list.png)

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
 * @return {ListNode}
 */
var deleteDuplicates = function(head) {
    let cur = head;
    while(cur && cur.next) {

        if(cur.val === cur.next.val) {
            cur.next = cur.next.next;
        } else {

            cur = cur.next;
        }
    }

    return head;
};
```

```java
/**
 * Definition for ListNode
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */


public class Solution {
    /*
     * @param head: head is the head of the linked list
     * @return: head of linked list
     */
    public ListNode deleteDuplicates(ListNode head) {
        
        ListNode cur = head;
       
        while (cur != null && cur.next != null) {
            
            if (cur.val == cur.next.val) {
                cur.next = cur.next.next;
            } else {
                cur = cur.next;
            }
            
        }
        
        
        return head;
    }
}
```



