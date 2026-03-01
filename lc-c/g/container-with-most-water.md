# Container With Most Water

Return the maximum amount of water a container can store.

```js
var maxArea = function (height) {
  let left = 0,
    right = height.length - 1,
    max = 0,
    area = 0
  while (left < right) {
    area = Math.min(height[left], height[right]) * (right - left)
    max = Math.max(area, max)
    if (height[left] < height[right]) {
      left += 1
    } else {
      right -= 1
    }
  }
  return max
}
```

O(N) and O(1)

https://leetcode.com/explore/interview/card/google/59/array-and-strings/3048/