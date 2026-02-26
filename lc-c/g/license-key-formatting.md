# License Key Formatting

You are given a license key represented as a string s that consists of only alphanumeric characters and dashes. The string is separated into n + 1 groups by n dashes. You are also given an integer k.

We want to reformat the string s such that each group contains exactly k characters, except for the first group, which could be shorter than k but still must contain at least one character. Furthermore, there must be a dash inserted between two groups, and you should convert all lowercase letters to uppercase.

```js
/**
 * @param {string} s
 * @param {number} k
 * @return {string}
 */
var licenseKeyFormatting = function (s, k) {
  let result = []
  let counter = 0
  for (var i = s.length - 1; i >= 0; i--) {
    let symbol = s[i].toUpperCase()
    if (counter < k) {
      if (symbol !== '-') {
        result.push(symbol)
        counter += 1
      }
    } else {
      if (symbol !== '-') {
        result.push('-')
        result.push(symbol)
        counter = 1
      }
    }
  }
  return result.reverse().join('')
}
```

Complexity O(N) and O(N)

https://leetcode.com/explore/interview/card/google/67/sql-2/472/