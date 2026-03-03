# Two Sum II - Input Array Is Sorted

Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number.

```js
var twoSum = function (numbers, target) {
  let left = 0,
    right = numbers.length - 1,
    last = 0

  do {
    last = numbers[left] + numbers[right]
    if (last === target) {
      return [left + 1, right + 1]
    } else if (last > target) {
      right -= 1
    } else {
      left += 1
    }
  } while (last != target)

  return [-1, -1]
}
```

O(N) and O(1)