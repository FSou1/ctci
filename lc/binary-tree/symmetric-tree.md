# Symmetric tree

Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

```
Input: root = [1,2,2,3,4,4,3]
Output: true
```

![alt text](https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg)

## Recursion solution

```js
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isSymmetric = function (root) {
  return check(root.left, root.right);
};

function check(left, right) {
  if (left == null && right == null) {
    return true;
  }

  if (left == null || right == null) {
    return false;
  }

  return (
    left.val == right.val &&
    check(left.left, right.right) &&
    check(left.right, right.left)
  );
}
```

https://leetcode.com/problems/symmetric-tree/description/
