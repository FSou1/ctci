# Longest Increasing Subsequence

Given an integer array nums, return the length of the longest strictly increasing subsequence.

## Solution 1

```js
var lengthOfLIS = function (nums) {
  let dp = new Array(nums.length).fill(1);

  for (let i = 1; i < nums.length; i++) {
    for (let j = 0; j < i; j++) {
      if (nums[i] > nums[j]) {
        dp[i] = Math.max(dp[i], dp[j] + 1);
      }
    }
  }

  let longest = 0;
  for (let el of dp) {
    longest = Math.max(longest, el);
  }

  return longest;
};
```

O(N^2) and O(N).
