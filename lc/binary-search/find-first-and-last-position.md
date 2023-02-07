# Find First and Last Position of Element in Sorted Array

Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.

## Solution

```js
var searchRange = function (nums, target) {
  if (nums.length === 0) return [-1, -1];

  const left = findLeftMostIndex(nums, target);

  if (left === -1) return [-1, -1];

  const right = findRightMostIndex(nums, target);

  return [left, right];
};

function findLeftMostIndex(nums, target) {
  let left = 0;
  let right = nums.length - 1;
  let leftMostIndex = -1;
  while (left <= right) {
    const mid = Math.trunc((left + right) / 2);
    if (nums[mid] > target) {
      right = mid - 1;
    } else if (nums[mid] < target) {
      left = mid + 1;
    } else {
      leftMostIndex = mid;
      right = mid - 1;
    }
  }
  return leftMostIndex;
}

function findRightMostIndex(nums, target) {
  let left = 0;
  let right = nums.length - 1;
  let rightMostIndex = -1;

  while (left <= right) {
    const mid = Math.trunc((left + right) / 2);
    if (nums[mid] > target) {
      right = mid - 1;
    } else if (nums[mid] < target) {
      left = mid + 1;
    } else {
      rightMostIndex = mid;
      left = mid + 1;
    }
  }
  return rightMostIndex;
}
```

O(logN) and O(1).
