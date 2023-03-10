# Rotate array

Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.

## Approach

Let's reverse an array once, then reverse the left and right parts.

```
Original List                   : 1 2 3 4 5 6 7
After reversing all numbers     : 7 6 5 4 3 2 1
After reversing first k numbers : 5 6 7 4 3 2 1
After revering last n-k numbers : 5 6 7 1 2 3 4 --> Result
```

## Solution

```js
var rotate = function (nums, k) {
  k = k % nums.length;
  reverse(nums, 0, nums.length - 1);
  reverse(nums, 0, k - 1);
  reverse(nums, k, nums.length - 1);
};

function reverse(nums, start, end) {
  while (start < end) {
    let z = nums[start];
    nums[start] = nums[end];
    nums[end] = z;
    start++;
    end--;
  }
}
```

O(N) and O(1)
