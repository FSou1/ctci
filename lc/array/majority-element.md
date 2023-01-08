# Majority Element

Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

## HashMap

```js
var majorityElement = function (nums) {
  let hash = {};
  for (let i = 0; i < nums.length; i++) {
    let elem = nums[i];
    if (!hash[elem]) {
      hash[elem] = 1;
    } else {
      hash[elem] += 1;
    }

    if (hash[elem] >= nums.length / 2) {
      return elem;
    }
  }
  return null;
};
```

O(N) and O(N).

## Boyer-Moore Voting Algorithm

If we had some way of counting instances of the majority element as +1+1+1 and instances of any other element as −1-1−1, summing them would make it obvious that the majority element is indeed the majority element.

[7, 7, 5, 7, 5, 1 | 5, 7 | 5, 5, 7, 7 | 7, 7, 7, 7]

```js
var majorityElement = function (nums) {
  let result = 0;
  for (var i = 0; i < nums.length; i++) {
    if (result == 0) {
      num = nums[i];
    }
    if (num === nums[i]) {
      result += 1;
    } else {
      result -= 1;
    }
  }
  return num;
};
```

https://leetcode.com/problems/majority-element/description/
