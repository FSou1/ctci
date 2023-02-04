# Min Stack

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the MinStack class:

- MinStack() initializes the stack object.
- void push(int val) pushes the element val onto the stack.
- void pop() removes the element on the top of the stack.
- int top() gets the top element of the stack.
- int getMin() retrieves the minimum element in the stack.

You must implement a solution with O(1) time complexity for each function.

## Solution

```js
var MinStack = function () {
  this.data = [];
  this.mins = [Number.POSITIVE_INFINITY];
};

function last(arr) {
  return arr[arr.length - 1];
}

MinStack.prototype.push = function (val) {
  this.data.push(val);
  if (val <= this.getMin()) {
    this.mins.push(val);
  }
};

MinStack.prototype.pop = function () {
  let val = this.data.pop();
  if (last(this.mins) === val) {
    this.mins.pop();
  }
};

MinStack.prototype.top = function () {
  return last(this.data);
};

MinStack.prototype.getMin = function () {
  return last(this.mins);
};
```
