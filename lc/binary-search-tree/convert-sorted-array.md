# Convert Sorted Array to Binary Search Tree

Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.

```
Input: nums = [-10,-3,0,5,9]
Output:
- [0,-3,9,-10,null,5]
- [0,-10,5,null,-3,null,9] is also accepted
```

![alt text](https://assets.leetcode.com/uploads/2021/02/18/btree2.jpg)

## Solution

```js
/**
 * @param {number[]} nums
 * @return {TreeNode}
 */
var sortedArrayToBST = function (nums) {
  return helper(nums, 0, nums.length - 1);
};

function helper(nums, left, right) {
  if (left > right) {
    return undefined;
  }

  let root = Math.floor((left + right) / 2);

  return new TreeNode(
    nums[root],
    helper(nums, left, root - 1),
    helper(nums, root + 1, right)
  );
}
```

O(N) and O(N).
