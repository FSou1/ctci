# Word Break

Given a string `s` and a dictionary of strings `wordDict`, return `true` if `s` can be segmented into a space-separated sequence of one or more dictionary words.

```
Input: s = "leetcode", wordDict = ["leet","code"]
Output: true
Explanation: Return true because "leetcode" can be segmented as "leet code".
```

This problem has various solutions and BFS is just one of them.

## BFS

```javascript
/**
 * @param {string} s
 * @param {string[]} wordDict
 * @return {boolean}
 */
var wordBreak = function (s, wordDict) {
  let to_visit = [0];
  let visited = [];
  while (to_visit.length > 0) {
    let start = to_visit.shift();
    if (visited[start]) {
      continue;
    }

    for (var end = start + 1; end <= s.length; end++) {
      let word = s.slice(start, end);
      if (wordDict.includes(word)) {
        to_visit.push(end);
      }
    }

    visited[start] = true;

    if (start === s.length) {
      return true;
    }
  }
  return false;
};
```
