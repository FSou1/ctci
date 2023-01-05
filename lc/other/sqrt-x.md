# Sqrt(x)

Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well.

You must not use any built-in exponent function or operator.

## Naive

```js
var mySqrt = function (x) {
  let start = 1;
  while (start * start <= x) {
    start += 1;
  }
  return start - 1;
};
```

## Binary search

```js
var mySqrt = function (x) {
  let low = Math.min(1, x),
    high = Math.max(1, x),
    mid = 0;
  for (let i = 0; i < 100; i++) {
    mid = Math.floor((low + high) / 2);
    if (mid * mid == x) return mid;
    if (mid * mid > x) high = mid;
    else low = mid;
  }
  return mid;
};
```

O(logN) and O(1).
