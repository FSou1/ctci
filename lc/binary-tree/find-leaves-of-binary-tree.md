# Find Leaves of Binary Tree

Given the root of a binary tree, collect a tree's nodes as if you were doing this:

- Collect all the leaf nodes.
- Remove all the leaf nodes.
- Repeat until the tree is empty.

## Solution 1 (deleting nodes in the tree)

```js
var findLeaves = function (root) {
  let result = [];
  while (root.left || root.right) {
    let iteration_result = [];
    getLeaves(root, iteration_result);
    result.push(iteration_result);
  }
  result.push([root.val]);
  return result;
};

function getLeaves(node, result) {
  if (!node) {
    return null;
  }

  if (!node.left && !node.right) {
    result.push(node.val);
    return null;
  }

  node.left = getLeaves(node.left, result);
  node.right = getLeaves(node.right, result);
  return node;
}
```

## Solution 2 - DFS (Depth-First Search) (calculate height)

```js
var findLeaves = function (root) {
  let result = [];
  getHeight(root, result);
  return result;
};

function getHeight(node, result) {
  if (!node) {
    return -1;
  }

  let leftHeight = getHeight(node.left, result);
  let rightHeight = getHeight(node.right, result);
  let currHeight = Math.max(leftHeight, rightHeight) + 1;

  if (result.length === currHeight) {
    result.push([]);
  }

  result[currHeight].push(node.val);

  return currHeight;
}
```
