# Shuffle an array

Given an integer array nums, design an algorithm to randomly shuffle the array. All permutations of the array should be equally likely as a result of the shuffling.

Implement the Solution class:

- `Solution(int[] nums)` Initializes the object with the integer array nums.
- `int[] reset()` Resets the array to its original configuration and returns it.
- `int[] shuffle()` Returns a random shuffling of the array.

## Solution

Fisher–Yates shuffle: https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle

![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5b/Durstenfeld_shuffle.svg/220px-Durstenfeld_shuffle.svg.png)

```js
/**
 * @param {number[]} nums
 */
var Solution = function (nums) {
  this.array = [...nums];
  this.original = [...nums];
};

/**
 * @return {number[]}
 */
Solution.prototype.reset = function () {
  this.array = [...this.original];
  return this.array;
};

/**
 * @return {number[]}
 */
Solution.prototype.shuffle = function () {
  const randomNumber = (min, max) =>
    Math.floor(Math.random() * (max - min) + min);

  for (let i = 0; i < this.array.length; i++) {
    this.swap(i, randomNumber(i, this.array.length));
  }

  return this.array;
};

Solution.prototype.swap = function (i, j) {
  let temp = this.array[i];
  this.array[i] = this.array[j];
  this.array[j] = temp;
};
```
