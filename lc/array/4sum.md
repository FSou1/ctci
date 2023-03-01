# 4Sum II

Given four integer arrays nums1, nums2, nums3, and nums4 all of length n, return the number of tuples (i, j, k, l) such that:

- 0 <= i, j, k, l < n
- nums1[i] + nums2[j] + nums3[k] + nums4[l] == 0

## Solution

```js
var fourSumCount = function (nums1, nums2, nums3, nums4) {
  let counter = 0;

  let hashSet1 = addUniqueSums(nums1, nums2);

  for (let x of nums3) {
    for (let y of nums4) {
      let key = -(x + y);
      if (hashSet1.hasOwnProperty(key)) {
        counter += hashSet1[key];
      }
    }
  }

  return counter;
};

function addUniqueSums(arr1, arr2) {
  let result = {};
  for (let el1 of arr1) {
    for (let el2 of arr2) {
      let sum = el1 + el2;
      result[sum] = (result[sum] || 0) + 1;
    }
  }
  return result;
}
```

O(N^2) and O(N^2).
