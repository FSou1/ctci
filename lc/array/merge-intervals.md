# Merge Intervals

Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

```
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
```

## Solution

```js
/**
 * @param {number[][]} intervals
 * @return {number[][]}
 */
var merge = function (intervals) {
  if (!intervals?.length) {
    return intervals;
  }

  let sortedIntervals = intervals.sort((a, b) => a[0] - b[0]);

  let result = [sortedIntervals[0]];

  let next = 1;
  while (sortedIntervals[next]) {
    let merged = mergeIntervals(
      result[result.length - 1],
      sortedIntervals[next]
    );

    if (merged) {
      result[result.length - 1] = merged;
    } else {
      result.push(sortedIntervals[next]);
    }

    next++;
  }

  return result;
};

var mergeIntervals = function (x, y) {
  let [xStart, xEnd] = x; // [1,3]... [1,4]... [1,4]... [1,4]
  let [yStart, yEnd] = y; // [2,10].. [0,4]... [0,0]... [0,2]

  if (xStart <= yStart && yStart <= xEnd) {
    return [xStart, Math.max(xEnd, yEnd)];
  }

  return null;
};
```
