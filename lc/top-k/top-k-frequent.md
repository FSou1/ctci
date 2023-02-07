# Top K frequent elements

Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

```
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

## Solution

```js
var topKFrequent = function (nums, k) {
  let result = [];

  let dict = {};
  for (const el of nums) {
    dict[el] = (dict[el] || 0) + 1;
  }

  let arr = Object.entries(dict);

  arr.sort((a, b) => {
    return b[1] - a[1];
  });

  arr.slice(0, k).forEach((element) => result.push(+element[0]));

  return result;
};
```

O(n log n) and O(N).
