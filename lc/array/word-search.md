# Word Search

Given an m x n grid of characters board and a string word, return true if word exists in the grid.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

```
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
Output: true
```

## Solution

```js
var exist = function (board, word) {
  for (let i = 0; i < board.length; i++) {
    for (let j = 0; j < board[0].length; j++) {
      let result = traverse(board, word, i, j, 0);
      if (result) {
        return true;
      }
    }
  }
  return false;
};

function traverse(board, word, i, j, wordIndex) {
  if (board?.[i]?.[j] != word[wordIndex]) {
    return false;
  }

  wordIndex += 1;

  if (word.length === wordIndex) {
    return true;
  }

  let newBoard = markVisited(board, i, j);

  return (
    traverse(newBoard, word, i + 1, j, wordIndex) ||
    traverse(newBoard, word, i, j + 1, wordIndex) ||
    traverse(newBoard, word, i - 1, j, wordIndex) ||
    traverse(newBoard, word, i, j - 1, wordIndex)
  );
}

function markVisited(board, i, j) {
  let updated = [...board.map((b) => [...b])];
  updated[i][j] = null;
  return updated;
}
```
