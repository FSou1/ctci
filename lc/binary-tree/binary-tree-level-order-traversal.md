# Binary Tree Level Order Traversal

Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

```
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]
```

![alt text](https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg)

## Solution

```js
var levelOrder = function (root) {
  let result = [];
  if (!root) {
    return result;
  }

  let queue = [root];
  do {
    result.push([]);

    let current = [...queue];
    queue = [];

    while (current.length) {
      let el = current.shift();

      result[result.length - 1].push(el.val);

      if (el.left) {
        queue.push(el.left);
      }
      if (el.right) {
        queue.push(el.right);
      }
    }
  } while (queue.length);

  return result;
};
```
