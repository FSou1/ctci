# Excel Sheet Column Number

Given a string columnTitle that represents the column title as appears in an Excel sheet, return its corresponding column number.

```
Input: columnTitle = "A"
Output: 1
```

```js
/**
 * @param {string} columnTitle
 * @return {number}
 */
var titleToNumber = function (columnTitle) {
  return columnTitle
    .split("")
    .reverse()
    .reduce((acc, cur, index) => {
      acc += (cur.charCodeAt(0) - 64) * Math.pow(26, index);
      return acc;
    }, 0);
};
```
