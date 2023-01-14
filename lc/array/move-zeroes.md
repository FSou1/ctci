# Move Zeroes

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

```
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```

## Solution

```js
var moveZeroes = function (nums) {
  let lastNonZeroFound = 0;
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] != 0) {
      nums[lastNonZeroFound++] = nums[i];
    }
  }

  for (let i = lastNonZeroFound; i < nums.length; i++) {
    nums[i] = 0;
  }
};
```

O(N) and O(1).
