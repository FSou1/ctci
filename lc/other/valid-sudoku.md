# Valid Sudoku

Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

- Each row must contain the digits 1-9 without repetition.
- Each column must contain the digits 1-9 without repetition.
- Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.

## Solution

```js
var isValidSudoku = function (board) {
  const N = board.length;

  let rows = new Array(N).fill(0).map((i) => new Set());
  let cols = new Array(N).fill(0).map((i) => new Set());
  let boxes = new Array(N).fill(0).map((i) => new Set());

  for (let i = 0; i < N; i++) {
    for (let j = 0; j < N; j++) {
      const val = board[i][j];
      if (val === ".") {
        continue;
      }

      if (rows[i].has(val)) {
        return false;
      }

      if (cols[j].has(val)) {
        return false;
      }

      const idx = Math.floor(i / 3) * 3 + Math.floor(j / 3);
      if (boxes[idx].has(val)) {
        return false;
      }

      rows[i].add(val);
      cols[j].add(val);
      boxes[idx].add(val);
    }
  }

  return true;
};
```

O(1) and O(1)
