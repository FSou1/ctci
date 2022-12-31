# Single Number

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function (nums) {
  let sum = 0;
  for (let elem of nums) {
    sum ^= elem;
  }
  return sum;
};
```

O(N) and O(N).

https://leetcode.com/problems/single-number/description/
