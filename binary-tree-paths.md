Given a binary tree, return all root-to-leaf paths.

**Example**

Given the following binary tree:

```
   1
 /   \
2     3
 \
  5

```

All root-to-leaf paths are:

```
[
  "1->2->5",
  "1->3"
]
```

```java
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
     * @param root: the root of the binary tree
     * @return: all root-to-leaf paths
     */
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> result = new ArrayList<String>();
        
        if (root == null) {
            return result;
        }
        
        //Depth First Search
        String list = "" + root.val;
        dfs(root, list, result);
        
        
        return result;
    }
    
    private void dfs(TreeNode node, String list, List<String> result) {
        
        // exit case
        if (node.left == null && node.right == null) {
            result.add(list);
        }
        
        // go left
        if (node.left != null) {
            String temp = list;
            list = list + "->" + node.left.val; // add to list
            dfs(node.left, list, result);
            list = temp;
        }
        
        // go right
        if (node.right != null) {
             String temp1 = list;
            list = list + "->" + node.right.val; // add to list
            dfs(node.right, list, result);
            list = temp1;
        }
        
    }
}
```



