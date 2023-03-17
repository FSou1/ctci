# Add Two Numbers

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

## Solution

```js
var addTwoNumbers = function (l1, l2) {
  let sum = 0;
  let current = new ListNode(0);
  let result = current;

  while (l1 || l2) {
    if (l1) {
      sum += l1.val;
      l1 = l1.next;
    }

    if (l2) {
      sum += l2.val;
      l2 = l2.next;
    }

    current.next = new ListNode(sum % 10);
    current = current.next;

    sum = sum > 9 ? 1 : 0;
  }

  if (sum) {
    current.next = new ListNode(sum);
  }

  return result.next;
};
```

## Solution (1565/1567 testcases passed)

The following solution doesn't pass a test case with a huge number (`[1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1]`):

```js
var addTwoNumbers = function (l1, l2) {
  let number1 = getNumber(l1);
  let number2 = getNumber(l2);
  return toList(number1 + number2);
};

function toList(number) {
  let prev = null,
    node = null;

  let str = number + "";
  for (let char of str) {
    node = new ListNode(char);
    if (prev) {
      node.next = prev;
      prev = node;
    } else {
      prev = node;
    }
  }

  return node;
}

function getNumber(node) {
  let result = 0;
  let digit = 0;
  let next = node;
  while (next) {
    result += next.val * Math.pow(10, digit++);
    next = next.next;
  }
  return result;
}
```
