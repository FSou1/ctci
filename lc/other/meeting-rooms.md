# Meeting rooms

Given an array of meeting time intervals where intervals[i] = [starti, endi], determine if a person could attend all meetings.

```
Input: intervals = [[0,30],[5,10],[15,20]]
Output: false
```

## Brute force solution

```js
var canAttendMeetings = function (intervals) {
  for (let i = 0; i < intervals.length; i++) {
    for (let j = i + 1; j < intervals.length; j++) {
      if (overlaps(intervals[i], intervals[j])) {
        return false;
      }
    }
  }

  return true;
};

function overlaps(interval1, interval2) {
  return (
    Math.max(interval1[0], interval2[0]) < Math.min(interval1[1], interval2[1])
  );
}
```

O(N^2) and O(1).

## Sorting

If you sort the intervals with O(NlogN) then need only O(N) to find an intersection.
