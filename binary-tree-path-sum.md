Given a binary tree, find all paths that sum of the nodes in the path equals to a given number`target`.

A valid path is from root node to any of the leaf nodes.

**Example**

Given a binary tree, and target =`5`:

```
     1
    / \
   2   4
  / \
 2   3

```

return

```
[
  [1, 2, 2],
  [1, 4]
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
     * @param root: the root of binary tree
     * @param target: An integer
     * @return: all valid paths
     */
    public List<List<Integer>> binaryTreePathSum(TreeNode root, int target) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        
        if (root == null) {
            return result;
        }
        
        //Depth First Search
        List<Integer> list = new ArrayList<Integer>();
        list.add(root.val);
        dfs(root, target-root.val, list, result);
        
        
        return result;
    }
    
    private void dfs(TreeNode node, int sum, List<Integer> list, List<List<Integer>> result) {
        
        // exit case
        if (node.left == null && node.right == null && sum == 0) {
            List<Integer> t = new ArrayList<Integer>();
            t.addAll(list);
            
            result.add(t);
        }
        
        // go left
        if (node.left != null) {
            list.add(node.left.val); // add to list
            dfs(node.left, sum-node.left.val, list, result);
            list.remove(list.size()-1); // remove from list
        }
        
        // go right
        if (node.right != null) {
            list.add(node.right.val); // add to list
            dfs(node.right, sum-node.right.val, list, result);
            list.remove(list.size()-1); // remove from list
        }
        
    }
}
```



