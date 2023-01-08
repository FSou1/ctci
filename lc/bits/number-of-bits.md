# Number of 1 Bits

## Basic Solution

```js
var hammingWeight = function (n) {
  return n.toString(2).replaceAll("0", "").length;
};
```

## Loop and flip

```js
var hammingWeight = function (n) {
  let mask = 1;
  let bits = 0;
  for (let i = 0; i < 32; i++) {
    if ((n & mask) != 0) {
      bits += 1;
    }
    mask <<= 1;
  }
  return bits;
};
```

https://leetcode.com/problems/number-of-1-bits
