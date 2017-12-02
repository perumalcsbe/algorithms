Count how many nodes in a linked list.

**Example**

Given`1->3->5`, return`3`.

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
     * @param head: the first node of linked list.
     * @return: An integer
     */
    public int countNodes(ListNode head) {
        int count = 0;
        
        while(head != null) {
            count++;
            head = head.next;
        }
        
        return count;
    }
}
```



