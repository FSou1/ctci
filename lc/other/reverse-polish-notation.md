# Evaluate Reverse Polish Notation

You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.

## Solution

```js
var evalRPN = function (tokens) {
  let queue = [tokens[0]];
  let index = 1;

  while (index < tokens.length) {
    queue.push(tokens[index++]);

    if (isOperator(queue[queue.length - 1])) {
      let operator = queue.pop();
      let b = queue.pop();
      let a = queue.pop();
      queue.push(getResult(a - 0, b - 0, operator));
    }
  }

  return queue[0];
};

var isOperator = function (symbol) {
  return ["+", "*", "-", "/"].includes(symbol);
};

var getResult = function (a, b, operator) {
  switch (operator) {
    case "*":
      return a * b;
    case "-":
      return a - b;
    case "+":
      return a + b;
    case "/":
      return Math.trunc(a / b);
  }
};
```
