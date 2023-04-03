# Maximum subarray

Given an integer array nums, find the subarray with the largest sum, and return its sum.

```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.
```

## Solution

```js
var maxSubArray = function (nums) {
  let max = nums[0];
  let balance = 0;
  for (let num of nums) {
    balance += num;
    max = Math.max(max, balance);
    if (balance < 0) {
      balance = 0;
    }
  }
  return max;
};
```

O(N) and O(1).
