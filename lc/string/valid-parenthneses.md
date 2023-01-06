# Valid Parentheses

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

```
Input: s = "()[]{}"
Output: true
```

```
Input: s = "(]"
Output: false
```

## Solution

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function (s) {
  let brackets = s.split("");
  let stack = [];
  for (var i = 0; i < brackets.length; i++) {
    let char = brackets[i];
    if (char == "(" || char == "[" || char == "{") {
      stack.push(char);
    } else {
      let last = getLast(stack);
      if (!isValidPair(char, last)) {
        return false;
      } else {
        stack.pop();
      }
    }
  }

  return stack.length === 0;
};

function isValidPair(current, last) {
  return (
    (current == ")" && last == "(") ||
    (current == "]" && last == "[") ||
    (current == "}" && last == "{")
  );
}

function getLast(arr) {
  return arr && arr[arr.length - 1];
}
```

O(N) and O(N).

https://leetcode.com/problems/valid-parentheses
