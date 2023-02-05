# Search a 2D Matrix II

Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:

- Integers in each row are sorted in ascending from left to right.
- Integers in each column are sorted in ascending from top to bottom.

![alt text](https://assets.leetcode.com/uploads/2020/11/24/searchgrid2.jpg)

## Solution

We move right > right > top > top until either:

- find the target element;
- fall outside of the dimensions of the matrix.

```js
var searchMatrix = function (matrix, target) {
  let row = matrix.length - 1;
  let col = 0;

  while (row >= 0 && col < matrix[0].length) {
    if (matrix[row][col] < target) {
      col++;
    } else if (matrix[row][col] > target) {
      row--;
    } else {
      return true;
    }
  }

  return false;
};
```

O(m+n) and O(1).
