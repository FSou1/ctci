# Maximum Depth of Binary Tree

Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

## Solution

```js
var maxDepth = function (root) {
  return treeDepth(root, 0);
};

function treeDepth(node, currentLevel) {
  if (!node) {
    return currentLevel;
  }

  return Math.max(
    treeDepth(node.left, currentLevel + 1),
    treeDepth(node.right, currentLevel + 1)
  );
}
```

https://leetcode.com/problems/maximum-depth-of-binary-tree/description/
