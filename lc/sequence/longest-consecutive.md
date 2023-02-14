# Longest consecutive sequence

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.

## Solution

```js
var longestConsecutive = function (nums) {
  if (!nums.length) {
    return 0;
  }

  let result = new Set();
  for (let i = 0; i < nums.length; i++) {
    result.add(nums[i]);
  }

  let longest = 0;

  for (let el of result) {
    if (!result.has(el - 1)) {
      let currentEl = el;
      let currentLongest = 0;

      while (result.has(currentEl++)) {
        currentLongest += 1;
      }

      longest = Math.max(longest, currentLongest);
    }
  }

  return longest;
};
```

O(N) and O(N).
