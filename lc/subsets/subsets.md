# Subsets

Given an integer array nums of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

```
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

## Solution

```js
var subsets = function (nums) {
  return createSubsets([], nums);
};

// - [], [1,2,3]
// - [1], [2,3]
// - [2], [3]
// - [3]
// - [1,2], [3]
// - [1,3]
// - [1,2,3]
var createSubsets = function (nums, queue) {
  let result = [nums];

  for (let i = 0; i < queue.length; i++) {
    let elem = queue[i];

    result = result.concat(
      createSubsets(nums.concat(elem), queue.slice(i + 1))
    );
  }

  return result;
};
```
