For the purposes of this challenge, we define a_binary search tree_to be a_binary tree_with the following ordering properties:

* The value of every node in a node's left subtree is _less than _the data value of that node.
* The value of every node in a node's right subtree is _greater than _the data value of that node.

Given the root node of a binary tree, can you determine if it's also a binary search tree?

Complete the function in your editor below, which has parameter: a pointer to the root of a binary tree. It must return a _boolean _denoting whether or not the binary tree is a binary search tree. You may have to write one or more helper functions to complete this challenge.

**Note: **We do not consider a binary tree to be a binary search tree if it contains duplicate values.

**Input Format**

You are not responsible for reading any input from stdin. Hidden code stubs will assemble a binary tree and pass its root node to your function as an argument.

**Output Format**

You are not responsible for printing any output to stdout. Your function must return _true _if the tree is a binary search tree; otherwise, it must return _false_. Hidden code stubs will print this result as a_Yes _or _No _answer on a new line.

**Sample Input**

![](https://testcases-diagram-generator.s3.amazonaws.com/undirected_graph/51b450a2f78262fb3326f379e08ec9dc "tree")

**Sample Output**

```
Yes

```

**Explanation**

The tree in the diagram satisfies the ordering property for a Binary Search Tree, so we print`Yes`.

```java
    int min;
    boolean checkBST(Node root) {
        if (root == null) {
            return true;
        }
        boolean left = checkBST(root.left);
        
        if (root.data <= min) {
            return false;
        }
        
        min = root.data;
        
        boolean right = checkBST(root.right);
        
        return left && right;
    }
```



