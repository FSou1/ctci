# Intersection of Two Arrays II

Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must appear as many times as it shows in both arrays and you may return the result in any order.

```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]
```

## HashMap

```js
var intersect = function (nums1, nums2) {
  let dict = {};
  for (let el of nums1) {
    if (dict[el]) {
      dict[el] += 1;
    } else {
      dict[el] = 1;
    }
  }

  let result = [];
  for (let el of nums2) {
    if (dict[el]) {
      result.push(el);
      dict[el] -= 1;
    }
  }
  return result;
};
```

## Sort

```js
var intersect = function (nums1, nums2) {
  let arr1 = nums1.sort((a, b) => a - b),
    arr2 = nums2.sort((a, b) => a - b),
    ind1 = 0,
    ind2 = 0;

  let result = [];
  while (ind1 < arr1.length && ind2 < arr2.length) {
    if (arr1[ind1] == arr2[ind2]) {
      result.push(arr1[ind1]);
      ind1 += 1;
      ind2 += 1;
    } else if (arr1[ind1] < arr2[ind2]) {
      ind1 += 1;
    } else {
      ind2 += 1;
    }
  }
  return result;
};
```

O(nlogn + mlogm) and O(logn + logm).

https://leetcode.com/problems/intersection-of-two-arrays-ii/description/
