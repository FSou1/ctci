# Missing Number

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

## Solution

```js
var missingNumber = function (nums) {
  let sum = 0,
    actual = 0;
  for (let i = 0; i < nums.length; i++) {
    sum += i;
    actual += nums[i];
  }
  sum += nums.length;
  return sum - actual;
};
```

O(N) and O(1).

https://leetcode.com/problems/missing-number/description/
