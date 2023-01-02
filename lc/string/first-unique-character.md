# First Unique Character in a String

Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1.

```
Input: s = "leetcode"
Output: 0
```

```js
/**
 * @param {string} s
 * @return {number}
 */
var firstUniqChar = function (s) {
  let dict = {};

  for (var char of s) {
    if (dict[char]) {
      dict[char] += 1;
    } else {
      dict[char] = 1;
    }
  }

  for (var i = 0; i < s.length; i++) {
    let char = s[i];
    if (dict[char] === 1) {
      return i;
    }
  }
  return -1;
};
```

O(N) and O(N).
