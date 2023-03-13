# Design Tic-Tac-Toe

Assume the following rules are for the tic-tac-toe game on an n x n board between two players:

A move is guaranteed to be valid and is placed on an empty block.

Once a winning condition is reached, no more moves are allowed.

A player who succeeds in placing n of their marks in a horizontal, vertical, or diagonal row wins the game.

Implement the TicTacToe class.

## Solution (ineffective)

```js
/**
 * @param {number} n
 */
var TicTacToe = function (n) {
  this.board = [...new Array(n)].fill().map((e) => [...new Array(n)]);
};

/**
 * @param {number} row
 * @param {number} col
 * @param {number} player
 * @return {number}
 */
TicTacToe.prototype.move = function (row, col, player) {
  this.board[row][col] = player;

  if (
    this.checkCol() ||
    this.checkRow() ||
    this.checkLRDiag() ||
    this.checkRLDiag()
  ) {
    return player;
  }

  return 0;
};

TicTacToe.prototype.checkCol = function () {
  let n = this.board.length;

  for (let i = 0; i < n; i++) {
    let winner1 = this.board.every((e) => e[i] === 1);
    let winner2 = this.board.every((e) => e[i] === 2);

    if (winner1 || winner2) {
      return true;
    }
  }

  return false;
};

TicTacToe.prototype.checkRow = function () {
  let n = this.board.length;

  for (let i = 0; i < n; i++) {
    let winner1 = this.board[i].every((e) => e === 1);
    let winner2 = this.board[i].every((e) => e === 2);

    if (winner1 || winner2) {
      return true;
    }
  }

  return false;
};

TicTacToe.prototype.checkLRDiag = function () {
  let n = this.board.length;

  let winner1 = true;
  let winner2 = true;

  for (let i = 0; i < n; i++) {
    if (this.board[i][i] != 1) {
      winner1 = false;
    }
    if (this.board[i][i] != 2) {
      winner2 = false;
    }
  }

  return winner1 || winner2;
};

TicTacToe.prototype.checkRLDiag = function () {
  let n = this.board.length;

  let winner1 = true;
  let winner2 = true;

  for (let i = n - 1, j = 0; i >= 0; i--, j++) {
    if (this.board[j][i] != 1) {
      winner1 = false;
    }
    if (this.board[j][i] != 2) {
      winner2 = false;
    }
  }

  return winner1 || winner2;
};
```

O(n) and O(n^2).
