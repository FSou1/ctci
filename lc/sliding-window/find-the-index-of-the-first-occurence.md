# Find the Index of the First Occurrence in a String

Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

## Solution 1

```js
var strStr = function (haystack, needle) {
  let current = 0;

  while (current < haystack.length) {
    let i = 0;
    while (haystack[current] != needle[i] && current < haystack.length) {
      current++;
    }

    while (haystack[current] === needle[i] && current < haystack.length) {
      current++;
      i++;
    }

    if (i === needle.length && haystack[current - 1] === needle[i - 1]) {
      return current - needle.length;
    }

    current = current - i + 1;
  }

  return -1;
};
```

O(NM) and O(1)

## Solution 2

```js
var strStr = function (haystack, needle) {
  let m = haystack.length,
    n = needle.length;

  for (let slidingWindow = 0; slidingWindow <= m - n; slidingWindow++) {
    for (let i = 0; i < n; i++) {
      if (haystack[slidingWindow + i] != needle[i]) {
        break;
      }
      if (i === n - 1) {
        return slidingWindow;
      }
    }
  }

  return -1;
};
```

O(NM) and O(1)
