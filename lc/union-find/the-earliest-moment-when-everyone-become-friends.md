# The Earliest Moment When Everyone Become Friends

There are n people in a social group labeled from 0 to n - 1. You are given an array logs.

Friendship is symmetric. That means if a is friends with b, then b is friends with a. Also, person a is acquainted with a person b if a is friends with b, or a is a friend of someone acquainted with b.

Return the earliest time for which every person became acquainted with every other person. If there is no such earliest time, return -1.

```
Input: logs = [[0,2,0],[1,0,1],[3,0,3],[4,1,2],[7,3,1]], n = 4
Output: 3
Explanation: At timestamp = 3, all the persons (i.e., 0, 1, 2, and 3) become friends.
```

## Solution

```js
var earliestAcq = function (logs, n) {
  let sorted = logs.sort((a, b) => a[0] - b[0]);

  let dict = [];
  for (let i = 0; i < n; i++) {
    dict[i] = [i];
  }

  for (let s of sorted) {
    let [ts, a, b] = s;
    if (!dict[a].includes(b)) {
      let group = [...dict[a], ...dict[b]];
      for (let num of group) {
        dict[num] = group;
      }
    }
    if (dict[a].length === n) return ts;
  }
  return -1;
};
```
