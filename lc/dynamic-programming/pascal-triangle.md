# Pascal's Triangle

Given an integer numRows, return the first numRows of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:

![alt text](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

```
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```

## Solution

```js
var generate = function (numRows) {
  let result = [[1]];

  for (let i = 1; i < numRows; i++) {
    let temp = new Array(i + 1).fill(0);

    for (let j = 0; j < temp.length; j++) {
      temp[j] = (result[i - 1][j - 1] || 0) + (result[i - 1][j] || 0);
    }

    result.push(temp);
  }

  return result;
};
```
