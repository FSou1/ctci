# Populating Next Right Pointers in Each Node

You are given a perfect binary tree where all leaves are on the same level, and every parent has two children. The binary tree has the following definition:

```
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```

Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

## Solution

```js
var connect = function (root) {
  let queue = [root];
  while (queue.length > 0) {
    let size = queue.length;
    for (let i = 0; i < size; i++) {
      let node = queue.shift();
      if (i < size - 1) {
        node.next = queue[0];
      }
      if (node?.left) queue.push(node.left);
      if (node?.right) queue.push(node.right);
    }
  }
  return root;
};
```

O(N) and O(N).
