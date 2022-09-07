# Middle of the linked list

Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

```
Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node of the list is node 3.
```

## Simple solution

`O(N)` and `O(N)` to hold an array of nodes, then `return A[t / 2]`, where `t` is the lenght of the list.

## Fast and slow pointer

A `slow` pointer traverses slow, while a `fast` pointer traverses twice as fast. When `fast` reaches the end of the list, `slow` must be in the middle:

```javascript
var middleNode = function(head) {
    let fast = head,
        slow = head;
    
    while(fast && fast.next) {
        fast = fast.next.next;
        slow = slow.next;
    }
    
    return slow;
};
```