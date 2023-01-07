# Reverse String

Write a function that reverses a string. The input string is given as an array of characters s.

You must do this by modifying the input array in-place with O(1) extra memory.

```
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```

```js
var reverseString = function (s) {
  let temp = "";
  for (var i = 0; i < s.length / 2; i++) {
    temp = s[i];
    s[i] = s[s.length - i - 1];
    s[s.length - i - 1] = temp;
  }
  return s;
};
```
