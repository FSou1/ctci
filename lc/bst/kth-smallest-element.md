# Kth Smallest Element in a BST

Given the root of a binary search tree, and an integer k, return the kth smallest value (1-indexed) of all the values of the nodes in the tree.

```
Input: root = [5,3,6,2,4,null,null,1], k = 3
Output: 3
```

![alt text](https://assets.leetcode.com/uploads/2021/01/28/kthtree2.jpg)

## DFS solution

The idea is to build an inorder traversal of BST which is an array sorted in the ascending order. Now the answer is the k - 1th element of this array.

```js
/**
 * @param {TreeNode} root
 * @param {number} k
 * @return {number}
 */
var kthSmallest = function (root, k) {
  let array = [];
  inorder(root, array);
  return array[k - 1];
};

function inorder(root, array) {
  if (root.left) {
    inorder(root.left, array);
  }

  array.push(root.val);

  if (root.right) {
    inorder(root.right, array);
  }
}
```

`O(N)` and `O(N)`.

https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/
