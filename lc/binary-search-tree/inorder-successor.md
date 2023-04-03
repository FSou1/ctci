# Inorder Successor in BST

Given the root of a binary search tree and a node p in it, return the in-order successor of that node in the BST. If the given node has no in-order successor in the tree, return null.

The successor of a node p is the node with the smallest key greater than p.val.

![](https://assets.leetcode.com/uploads/2019/01/23/285_example_1.PNG)

```
Input: root = [2,1,3], p = 1
Output: 2
Explanation: 1's in-order successor node is 2. Note that both p and the return value is of TreeNode type.
```

## Solution

```js
var inorderSuccessor = function (root, p) {
  return findNode(root, p.val, null);
};

function findNode(root, target, result) {
  if (!root) {
    return result;
  }

  if (root.val > target) {
    result = root;
    return findNode(root.left, target, result);
  }

  if (root.val <= target) {
    return findNode(root.right, target, result);
  }
}
```
