# Unique Paths

There is a robot on an m x n grid. The robot is initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., grid[m - 1][n - 1]). The robot can only move either down or right at any point in time.

Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.

## Solution

```js
var uniquePaths = function (m, n) {
  let result = Array(m)
    .fill()
    .map(() => Array(n).fill(0));
  result[0][0] = 1;
  for (let i = 0; i < m; i++) {
    for (let j = 0; j < n; j++) {
      if (i - 1 >= 0) {
        result[i][j] += result[i - 1][j];
      }
      if (j - 1 >= 0) {
        result[i][j] += result[i][j - 1];
      }
    }
  }
  return result[m - 1][n - 1];
};
```

O(M x N) and O(M x N).
