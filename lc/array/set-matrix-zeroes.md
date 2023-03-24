# Set Matrix Zeroes

Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.

```
Input: matrix = [[1,1,1],[1,0,1],[1,1,1]]
Output: [[1,0,1],[0,0,0],[1,0,1]]
```

## Solution

```js
var setZeroes = function (matrix) {
  let rows = {};
  let columns = {};
  for (let i = 0; i < matrix.length; i++) {
    for (let j = 0; j < matrix[i].length; j++) {
      if (matrix[i][j] === 0) {
        rows[i] = true;
        columns[j] = true;
      }
    }
  }

  for (let row in rows) {
    for (let j = 0; j < matrix[row].length; j++) {
      matrix[row][j] = 0;
    }
  }

  for (let col in columns) {
    for (let i = 0; i < matrix.length; i++) {
      matrix[i][col] = 0;
    }
  }
};
```

O(M x N) and O(M + N).
