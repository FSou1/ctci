# Linked List Cycle II

Given the `head` of a linked list, return the `node` where the cycle begins. If there is no cycle, return `null`.

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

## Simple solution

`O(N)` and `O(N)` to track the visited nodes.

```javascript
var detectCycle = function(head) {
    let visited = new Set();
    
    let node = head;

    while(node != null) {
        if(visited.has(node)) {
            return node;
        }
        visited.add(node);
        node = node.next
    }
    
    return null;
};
```

## Floyd's Tortoise and Hare

`O(N)` and `O(1)`.

```javascript
TBD
```