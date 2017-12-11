Find the maximum node in a binary tree, return the node.

**Example**

Given a binary tree:

```
     1
   /   \
 -5     2
 / \   /  \
0   3 -4  -5
```

return the node with value`3`.

```
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */
public class Solution {
    /*
     * @param root: the root of tree
     * @return: the max node
     */
    public TreeNode maxNode(TreeNode root) {
       if (root == null) {
           return null;
       }
       
       Queue<TreeNode> q = new LinkedList<TreeNode>();
       q.add(root);
       int max = Integer.MIN_VALUE;
       TreeNode result = null;
       while(!q.isEmpty()) {
           TreeNode node = q.poll(); // remove head
           if (max < node.val) {
               max = node.val;
               result = node;
           }
           if (node.left != null) {
               q.add(node.left);
           }
           
           if (node.right != null) {
               q.add(node.right);
           }
       }
        
        return result;
    }
}
```



