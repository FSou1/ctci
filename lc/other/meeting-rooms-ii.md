# Meeting Rooms II

Given an array of meeting time intervals intervals where intervals[i] = [starti, endi], return the minimum number of conference rooms required.

```
Input: intervals = [[0,30],[5,10],[15,20]]
Output: 2
```

## Solution

> When we encounter an ending event, that means that some meeting that started earlier has ended now. We are not really concerned with which meeting has ended. All we need is that some meeting ended thus making a room available.

![img](https://leetcode.com/problems/meeting-rooms-ii/Figures/253/253_Meeting_Rooms_II_Diag_4.png)

```js
var minMeetingRooms = function (intervals) {
  let starts = intervals.sort((a, b) => a[0] - b[0]).map((arr) => arr[0]);

  let ends = intervals.sort((a, b) => a[1] - b[1]).map((arr) => arr[1]);

  let numberRooms = 0;

  let sPtr = 0,
    ePtr = 0;
  while (sPtr < starts.length) {
    if (starts[sPtr] >= ends[ePtr]) {
      numberRooms -= 1;
      ePtr += 1;
    }

    numberRooms += 1;
    sPtr += 1;
  }

  return numberRooms;
};
```

O(NlogN) and O(N).
