# Longest Palindromic Substring

Given a string s, return the longest palindromic substring in s.

```
Input: s = "babad"
Output: "bab"
Explanation: "aba" is also a valid answer.
```

```
Input: s = "cbbd"
Output: "bb"
```

## Solution 1 (brute force)

```js
var longestPalindrome = function (s) {
  let longest = "";

  for (let i = 0; i < s.length; i++) {
    for (let j = s.length - 1; i <= j; j--) {
      let term = s.slice(i, j + 1);
      if (isPalindrome(term) && term.length > longest.length) {
        longest = term;
      }
    }
  }

  return longest;
};

function isPalindrome(s) {
  for (let i = 0, j = s.length - 1; i < j; i++, j--) {
    if (s[i] != s[j]) {
      return false;
    }
  }
  return true;
}
```

O(N^3) and O(1).

## Expand Around Center

```js
var longestPalindrome = function (s) {
  let longest = "";

  for (let i = 0; i < s.length; i++) {
    let single = findOuter(s, i, i);
    let double = findOuter(s, i, i + 1);
    longest = single.length > longest.length ? single : longest;
    longest = double.length > longest.length ? double : longest;
  }

  return longest;
};

function findOuter(s, start, end) {
  if (s[start] != s[end]) {
    return "";
  }

  let L = start,
    R = end;

  if (s[--L] === s[++R] && s[L] != undefined) {
    return findOuter(s, L, R);
  }

  return s.slice(start, end + 1);
}
```

O(N^2) and O(1).
