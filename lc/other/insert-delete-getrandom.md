# Insert Delete GetRandom O(1)

Implement the RandomizedSet class:

- RandomizedSet() Initializes the RandomizedSet object.
- bool insert(int val) Inserts an item val into the set if not present. Returns true if the item was not present, false otherwise.
- bool remove(int val) Removes an item val from the set if present. Returns true if the item was present, false otherwise.
- int getRandom() Returns a random element from the current set of elements (it's guaranteed that at least one element exists when this method is called). Each element must have the same probability of being returned.

You must implement the functions of the class such that each function works in average O(1) time complexity.

## Solution

```js
var RandomizedSet = function () {
  this.dict = {};
  this.list = [];
};

/**
 * @param {number} val
 * @return {boolean}
 */
RandomizedSet.prototype.insert = function (val) {
  if (this.dict.hasOwnProperty(val)) {
    return false;
  }
  this.dict[val] = this.list.length;
  this.list[this.list.length] = val;
  return true;
};

/**
 * @param {number} val
 * @return {boolean}
 */
RandomizedSet.prototype.remove = function (val) {
  if (!this.dict.hasOwnProperty(val)) {
    return false;
  }
  let index = this.dict[val];
  this.list[index] = this.list[this.list.length - 1];
  this.dict[this.list[index]] = index;
  delete this.dict[val];
  this.list.length -= 1;
  return true;
};

/**
 * @return {number}
 */
RandomizedSet.prototype.getRandom = function () {
  return this.list[getRandomInt(0, this.list.length - 1)];
};

function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
```
