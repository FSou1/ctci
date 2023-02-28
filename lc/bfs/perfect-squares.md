# Perfect Squares

Given an integer n, return the least number of perfect square numbers that sum to n.

A perfect square is an integer that is the square of an integer; in other words, it is the product of some integer with itself. For example, 1, 4, 9, and 16 are perfect squares while 3 and 11 are not.

```
Input: n = 12
Output: 3
Explanation: 12 = 4 + 4 + 4.
```

## Solution

![](https://leetcode.com/problems/perfect-squares/Figures/279/279_greedy_bfs_edited.png)

```js
var numSquares = function (n) {
  let squares = getSquares(n);

  let queue = [n];
  let level = 0;

  while (queue.length > 0) {
    level += 1;
    let next_queue = [];

    for (let remainder of queue) {
      for (let square of squares) {
        if (remainder === square) {
          return level;
        } else if (remainder < square) {
          break;
        } else {
          next_queue.push(remainder - square);
        }
      }
    }

    queue = next_queue;
  }

  return level;
};

function getSquares(n) {
  let result = [];
  for (let i = 1; i * i <= n; i++) {
    result.push(i * i);
  }
  return result;
}
```
