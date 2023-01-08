# Palindrome Linked List

Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

```js
var isPalindrome = function (head) {
  let str = "";
  while (head) {
    str += head.val;
    head = head.next;
  }

  for (var i = 0; i <= str.length / 2; i++) {
    if (str[i] != str[str.length - i - 1]) {
      return false;
    }
  }

  return true;
};
```

O(N) and O(N).

https://leetcode.com/problems/palindrome-linked-list/description/
