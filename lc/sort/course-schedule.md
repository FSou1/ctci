# Course Schedule

There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

```
Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
Output: false
Explanation: There are a total of 2 courses to take.
To take course 1 you should have finished course 0, and to take course 0 you should also have finished course 1. So it is impossible.
```

## Solution

Topological sort.

```js
var canFinish = function (numCourses, prerequisites) {
  let mapped = [];
  for (let [a, b] of prerequisites) {
    mapped[a] = (mapped[a] || 0) + 1;

    if (!mapped.hasOwnProperty(b)) {
      mapped[b] = 0;
    }
  }

  let queue = [];
  for (let course = 0; course < mapped.length; course++) {
    let reqs = mapped[course];
    if (reqs === 0) {
      queue.push(course);
    }
  }

  while (queue.length) {
    let currentCourse = queue.pop();
    for (let [a, b] of prerequisites) {
      if (currentCourse === b) {
        mapped[a] -= 1;
        if (mapped[a] === 0) {
          queue.push(a);
        }
      }
    }
  }

  return !mapped.some((reqs) => reqs > 0);
};
```
