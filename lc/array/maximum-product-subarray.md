# Maximum Product Subarray

Given an integer array nums, find a subarray that has the largest product, and return the product.

## Naive

```js
var maxProduct = function (nums) {
  if (nums.length == 1) {
    return nums[0];
  }

  let max = 0;
  for (let i = 0; i < nums.length; i++) {
    let result = nums[i];
    if (result > max) {
      max = result;
    }

    for (let j = i + 1; j < nums.length; j++) {
      result *= nums[j];
      if (result > max) {
        max = result;
      }
    }
  }

  return max;
};
```

O(N^2) and O(1)

## Double iteration

```js
var maxProduct = function (nums) {
  if (nums.length == 1) {
    return nums[0];
  }

  let max = nums[0];
  let result = 1;
  for (let i = 0; i < nums.length; i++) {
    result *= nums[i];
    max = Math.max(max, result);
    if (result == 0) result = 1;
  }

  result = 1;
  for (let j = nums.length - 1; j > 0; j--) {
    result *= nums[j];
    max = Math.max(max, result);
    if (result == 0) result = 1;
  }

  return max;
};
```

O(2N) and O(1).

## Dynamic programming

![](https://img001.prntscr.com/file/img001/keS7XOxIQPKOCKV-L-hSyQ.png)

```js
var maxProduct = function (nums) {
  if (nums.length == 0) return 0;

  let max_so_far = nums[0];
  let min_so_far = nums[0];
  let result = max_so_far;

  for (let i = 1; i < nums.length; i++) {
    let current = nums[i];

    let temp_max = Math.max(
      current,
      Math.max(current * max_so_far, current * min_so_far)
    );

    min_so_far = Math.min(
      current,
      Math.min(current * max_so_far, current * min_so_far)
    );

    max_so_far = temp_max;

    result = Math.max(max_so_far, result);
  }

  return result;
};
```

O(N) and O(1).
