# Decode String

Given an encoded string, return its decoded string.

The encoding rule is: k[encoded_string], where the encoded_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a positive integer.

```
Input: s = "3[a]2[bc]"
Output: "aaabcbc"
```

## Solution

```js
var decodeString = function (s) {
  // 3[a]2[bc]
  // step1: 3[a] -> aaa2[bc]
  // step2: aaa2[bc] -> aaabcbc
  let result = s,
    match = null;

  while ((match = result.match("([0-9]+\\[[a-z]+\\])"))) {
    let decoded = decodeWord(match[0]);
    result = result.replaceAll(match[0], decoded);
  }

  return result;
};

function decodeWord(s) {
  let number = s.replace(/\D+/g, "");
  let characters = s.replace(/[^a-z]/gi, "");
  return characters.repeat(number);
}
```
