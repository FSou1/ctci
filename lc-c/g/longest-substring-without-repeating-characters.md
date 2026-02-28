# Longest Substring Without Repeating Characters

Given a string s, find the length of the longest substring without duplicate characters.

```js
var lengthOfLongestSubstring = function(s) {
    const dict = new Map();
    let i = 0, j = 0;
    let max_length = 0;
    while(i < s.length) {
        const letter = s[i];
        if((dict.get(letter) || 0) === 0) {
            dict.set(letter, 1);
            max_length = Math.max(i - j + 1, max_length);
        } else {
            dict.set(letter, dict.get(letter) + 1);
            while(dict.get(letter) > 1) {
                dict.set(s[j], dict.get(s[j]) - 1);
                j++;
            }
        }
        i++;
    }
    return max_length;
};
```

https://leetcode.com/explore/interview/card/google/59/array-and-strings/3047/