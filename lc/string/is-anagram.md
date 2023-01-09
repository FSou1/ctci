# Valid Anagram

Given two strings s and t, return true if t is an anagram of s, and false otherwise.

## HashMap

```js
var isAnagram = function (s, t) {
  if (s.length != t.length || !s || !t) {
    return false;
  }

  let sDict = toDict(s);
  let tDict = toDict(t);

  return equal(sDict, tDict);
};

function toDict(str) {
  return str.split("").reduce((acc, cur) => {
    acc[cur] = (acc[cur] || 0) + 1;
    return acc;
  }, {});
}

function equal(dict1, dict2) {
  let keys = Object.keys(dict1);
  for (let key of keys) {
    if (!dict2[key] || dict1[key] != dict2[key]) {
      return false;
    }
  }
  return true;
}
```

O(N) and O(N).

## Array

```js
var isAnagram = function (s, t) {
  if (s.length != t.length || !s || !t) {
    return false;
  }

  const aCode = 97;

  let arr = new Array(26).fill(0);
  for (let i = 0; i < s.length; i++) {
    arr[s.charCodeAt(i) - aCode] += 1;
    arr[t.charCodeAt(i) - aCode] -= 1;
  }

  for (let el of arr) {
    if (el != 0) {
      return false;
    }
  }

  return true;
};
```

O(N) and O(N).

https://leetcode.com/problems/valid-anagram/description/
