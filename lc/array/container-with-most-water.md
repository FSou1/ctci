# Container With Most Water

You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

## Solution

```js
var maxArea = function (height) {
  let left = 0,
    right = height.length - 1;
  let max = 0;
  while (left != right) {
    let min = Math.min(height[left], height[right]);
    let current = min * (right - left);
    max = Math.max(max, current);
    height[left] < height[right] ? left++ : right--;
  }
  return max;
};
```

O(N) and O(1).
