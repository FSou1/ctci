# Palindrome Linked List

Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

```
Input: head = [1,2,2,1]
Output: true
```

## Solution (Advanced)

In order to complete a task with an O(1) space complexity, an algorithm should update the linked list in place. Additionally, to avoid any unwanted side-effects, the algorithm should restore the initial state once the task is finished.

O(N) and O(1).

```js
var isPalindrome = function (head) {
  if (!head) return true;

  // find middle
  let endOfFirstHalf = findEndOfFirstHalf(head);

  // reverse(middle)
  let reversedSecondHalf = reverseList(endOfFirstHalf.next);

  // compare(head, middle)
  let result = compare(head, reversedSecondHalf);

  // reverse(middle)
  endOfFirstHalf.next = reverseList(reversedSecondHalf);

  // return
  return result;
};

function findEndOfFirstHalf(head) {
  let slow = head,
    fast = head;

  while (fast.next != null && fast.next.next != null) {
    slow = slow.next;
    fast = fast.next.next;
  }

  return slow;
}

function reverseList(head) {
  let prev = null;
  let curr = head;

  while (curr != null) {
    let temp = curr.next;
    curr.next = prev;
    prev = curr;
    curr = temp;
  }

  return prev;
}

function compare(node1, node2) {
  let left = node1,
    right = node2;

  while (right != null) {
    if (left.val !== right.val) {
      return false;
    }

    left = left.next;
    right = right.next;
  }

  return true;
}
```

## Solution (Basic)

O(N) and O(N).

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

https://leetcode.com/problems/palindrome-linked-list/description/
