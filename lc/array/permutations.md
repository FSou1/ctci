# Permutations

Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

## Solution

```js
var permute = function (nums) {
  let result = [];

  iterate(nums, [], result);

  return result;
};

function iterate(array, current, result) {
  if (!array.length) {
    result.push(current);
    return;
  }

  for (let i = 0; i < array.length; i++) {
    iterate(
      array.filter((el, idx) => i !== idx),
      [...current, array[i]],
      result
    );
  }
}
```
