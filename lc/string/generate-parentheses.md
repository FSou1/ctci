# Generate Parentheses

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

```
Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]
```

## Solution

```js
var generateParenthesis = function (n) {
  let result = [];
  getNext("", n, n, 0, result);
  return result;
};

function getNext(currentString, open, close, hasOpened, result) {
  if (open === 0 && close === 0) {
    result.push(currentString);
    return;
  }

  if (open > 0) {
    getNext(currentString + "(", open - 1, close, hasOpened + 1, result);
  }

  let last = currentString[currentString.length - 1];

  if (last === "(" && close > 0) {
    getNext(currentString + ")", open, close - 1, hasOpened - 1, result);
  }

  if (last === ")" && hasOpened > 0) {
    getNext(currentString + ")", open, close - 1, hasOpened - 1, result);
  }
}
```
