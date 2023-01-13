# Binary Tree Inorder Traversal

Given the root of a binary tree, return the inorder traversal of its nodes' values.

> Inorder Traversal. An inorder traversal first visits the left child (including its entire subtree), then visits the node, and finally visits the right child (including its entire subtree).

```
Input: root = [1,null,2,3]
Output: [1,3,2]
```

## Solution

```js
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var inorderTraversal = function (root) {
  return traverse(root, []);
};

function traverse(node, values) {
  if (!node) {
    return values;
  }

  values.concat(traverse(node.left, values));
  values.push(node.val);
  values.concat(traverse(node.right, values));

  return values;
}
```

https://leetcode.com/problems/binary-tree-inorder-traversal/description/
