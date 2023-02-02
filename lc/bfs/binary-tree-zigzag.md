# Binary Tree Zigzag Level Order Traversal

Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).

![](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/solutions/461703/Figures/103/103_BFS.png)

## Solution

```js
var zigzagLevelOrder = function (root) {
  if (!root) {
    return [];
  }

  let result = [];

  let queue = [];
  queue.push(root);

  let even = true;
  while (queue.length > 0) {
    let n = queue.length;
    let subList = [];

    for (let i = 0; i < n; i++) {
      let top = queue.shift();

      if (top.left != null) {
        queue.push(top.left);
      }
      if (top.right != null) {
        queue.push(top.right);
      }
      if (even) {
        subList.push(top.val);
      } else {
        subList.unshift(top.val);
      }
    }
    result.push(subList);
    even = !even;
  }

  return result;
};
```

O(N) and O(N).
