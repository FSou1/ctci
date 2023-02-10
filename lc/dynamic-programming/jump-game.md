# Jump Game

You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.

## Solution

```js
var canJump = function (nums) {
  if (nums.length == 1) {
    return true;
  }

  let dp = new Array(nums.length).fill(false);

  let curr = nums.length - 1;
  while (curr > 0) {
    let prev = curr;
    while (prev-- >= 0) {
      if (prev + nums[prev] >= curr) {
        dp[curr] = true;
        break;
      }
    }
    if (!dp[curr]) {
      return false;
    }
    curr--;
  }

  return nums[0] > 0;
};
```

O(N^2) and O(N).
