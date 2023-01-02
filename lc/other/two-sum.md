# Two Sum

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function (nums, target) {
  let dict = {};
  for (let i = 0; i < nums.length; i++) {
    let num = nums[i];
    let need = target - num;
    if (dict.hasOwnProperty(need)) {
      return [i, dict[need]];
    }

    dict[num] = i;
  }
};
```
