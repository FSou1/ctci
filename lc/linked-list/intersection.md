# Intersection of Two Linked Lists

Given the heads of two singly linked-lists headA and headB, return the node at which the two lists intersect. If the two linked lists have no intersection at all, return null.

For example, the following two linked lists begin to intersect at node c1:

![](https://assets.leetcode.com/uploads/2021/03/05/160_statement.png)

## Solution

```js
/**
 * @param {ListNode} headA
 * @param {ListNode} headB
 * @return {ListNode}
 */
var getIntersectionNode = function (headA, headB) {
  let visited = new Set();

  let left = headA,
    right = headB;

  while (left) {
    visited.add(left);
    left = left.next;
  }

  while (right) {
    if (visited.has(right)) {
      return right;
    }
    visited.add(right);
    right = right.next;
  }
};
```

O(M+N) and O(M);

## Tricky solution

```java
public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
  ListNode pA = headA;
  ListNode pB = headB;
  while (pA != pB) {
    pA = pA == null ? headB : pA.next;
    pB = pB == null ? headA : pB.next;
  }
  return pA;
  // Note: In the case lists do not intersect, the pointers for A and B
  // will still line up in the 2nd iteration, just that here won't be
  // a common node down the list and both will reach their respective ends
  // at the same time. So pA will be NULL in that case.
}
```

O(2 x M + 2 x N) = O(M+N) and O(1).
