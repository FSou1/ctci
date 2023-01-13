# Reverse Linked List

Given the head of a singly linked list, reverse the list, and return the reversed list.

```js
var reverseList = function (head) {
  let prev = null;
  let curr = head;

  while (curr != null) {
    let temp = curr.next;
    curr.next = prev;
    prev = curr;
    curr = temp;
  }

  return prev;
};
```

O(N) and O(1).
