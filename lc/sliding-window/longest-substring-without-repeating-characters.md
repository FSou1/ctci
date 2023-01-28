# Longest Substring Without Repeating Characters

Given a string s, find the length of the longest substring without repeating characters.

```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

## Solution

```js
var lengthOfLongestSubstring = function (s) {
  let longest = 0;

  let left = 0,
    right = 0,
    dict = {};
  while (right < s.length) {
    let char = s[right];

    dict[char] = (dict[char] ?? 0) + 1;

    while (dict[char] > 1) {
      dict[s[left++]] -= 1;
    }

    longest = Math.max(longest, right - left + 1);

    right += 1;
  }

  return longest;
};
```
