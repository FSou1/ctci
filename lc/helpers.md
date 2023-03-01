# Code snippets

## String to array

`s.split('')`

## Array to hashset by count

```javascript
function groupByCount(arr) {
  return arr.reduce((acc, cur) => {
    acc[cur] = (acc[cur] || 0) + 1;
    return acc;
  }, {});
}
```
