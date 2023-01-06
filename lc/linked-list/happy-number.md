# Happy Number

Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

Starting with any positive integer, replace the number by the sum of the squares of its digits.

Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.

Those numbers for which this process ends in 1 are happy.

Return true if n is a happy number, and false if not.

```
Input: n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

## Basic solution

```javascript
var isHappy = function (n) {
  let next = n;
  for (let i = 0; i < 100; i++) {
    next = getNext(next);
    if (next === 1) {
      return true;
    }
  }
  return false;
};

function getNext(n) {
  return (n + "").split("").reduce((acc, cur) => (acc += cur * cur), 0);
}
```

## Floyd's Cycle-Finding Algorithm

The chain we get by repeatedly calling getNext(n) is an implicit LinkedList.

Like in [Linked List Cycle II](./happy-number.md), when we used this algorithm to find a cycle in a linked list, we can use it here as well.

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function (n) {
  let slow = n,
    fast = getNext(n);

  while (slow != fast) {
    slow = getNext(slow);
    fast = getNext(getNext(fast));
  }

  return slow === 1;
};

function getNext(n) {
  return (n + "").split("").reduce((acc, cur) => (acc += cur * cur), 0);
}
```

https://leetcode.com/problems/happy-number
