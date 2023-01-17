# Wiggle Sort II

Given an integer array nums, reorder it such that nums[0] < nums[1] > nums[2] < nums[3]....

You may assume the input array always has a valid answer.

```
Input: nums = [1,5,1,1,6,4]
Output: [1,6,1,5,1,4]
Explanation: [1,4,1,5,1,6] is also accepted.
```

```js
var wiggleSort = function (nums) {
  let arr = [...nums];
  arr.sort((a, b) => a - b);
  let n = nums.length;
  let i = (n - 1) >> 1,
    j = n - 1;
  for (let x = 0; x < nums.length; x++) {
    if (x % 2 == 0) {
      nums[x] = arr[i--];
    } else {
      nums[x] = arr[j--];
    }
  }
};
```

https://leetcode.com/problems/wiggle-sort-ii
