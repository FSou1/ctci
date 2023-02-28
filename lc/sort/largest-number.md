# Largest Number

Given a list of non-negative integers nums, arrange them such that they form the largest number and return it.

```
Input: nums = [3,30,34,5,9]
Output: "9534330"
```

## Solution

```js
var largestNumber = function (nums) {
  let sorted = nums.sort(compare);

  let result = sorted.join("");
  if (result[0] === "0") {
    return "0";
  }

  return result;
};

function compare(a, b) {
  let aStr = `${b}${a}` - 0;
  let bStr = `${a}${b}` - 0;
  return aStr - bStr;
}
```

O(nlogn) and O(n)
