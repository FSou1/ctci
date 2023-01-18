# Odd Even Linked List

Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.

The first node is considered odd, and the second node is even, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

You must solve the problem in O(1) extra space complexity and O(n) time complexity.

```
Input: head = [1,2,3,4,5]
Output: [1,3,5,2,4]
```

## Solution

```js
var oddEvenList = function (head) {
  if (!head?.next) {
    return head;
  }

  let evenHead = head.next;

  reorderList(head, head.next, evenHead);

  return head;
};

function reorderList(odd, even, evenHead) {
  let nextOdd = even?.next;
  if (nextOdd) {
    odd.next = nextOdd;
  } else {
    odd.next = null;
  }

  let nextEven = nextOdd?.next;
  if (nextEven) {
    even.next = nextEven;
  } else {
    even.next = null;
  }

  if (nextEven && nextOdd) {
    reorderList(odd.next, even.next, evenHead);
  }

  if (!nextOdd) {
    odd.next = evenHead;
  }

  if (!nextEven && nextOdd) {
    nextOdd.next = evenHead;
  }
}
```
