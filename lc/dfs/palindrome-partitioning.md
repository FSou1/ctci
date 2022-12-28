# Palindrome Partitioning

Given a string s, partition s such that every substring of the partition is a palindrome.

Return all possible palindrome partitioning of s.

```
Input: s = "aab"
Output: [["a","a","b"],["aa","b"]]
```

```
Input: s = "a"
Output: [["a"]]
```

## Solution

```javascript
/**
 * @param {string} s
 * @return {string[][]}
 */
var partition = function (s) {
  let result = [];
  dfs(0, result, [], s);
  return result;
};

function dfs(start, result, currentList, s) {
  if (start >= s.length) {
    result.push([...currentList]);
  }

  for (let end = start; end < s.length; end++) {
    let str = s.slice(start, end + 1);
    if (isPalindrom(str)) {
      currentList.push(str);
      dfs(end + 1, result, currentList, s);
      currentList.pop();
    }
  }
}

function isPalindrom(str) {
  return str == str.split("").reverse().join("");
}
```

https://leetcode.com/problems/palindrome-partitioning/
