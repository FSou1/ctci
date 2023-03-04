# Course Schedule II

There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.

Return the ordering of courses you should take to finish all courses. If there are many valid answers, return any of them. If it is impossible to finish all courses, return an empty array.

## Solution

Kahn’s algorithm for Topological Sorting

```js
var findOrder = function (numCourses, prerequisites) {
  let inDegree = new Array(numCourses).fill(0);
  for (let [v] of prerequisites) {
    inDegree[v]++;
  }

  const q = [];
  for (let i = 0; i < inDegree.length; i++) {
    if (inDegree[i] === 0) {
      q.push(i);
    }
  }

  const res = [];
  while (q.length) {
    let elem = q.shift();
    res.push(elem);
    numCourses--;
    for (let [a, b] of prerequisites) {
      if (elem === b) {
        inDegree[a]--;
        if (inDegree[a] === 0) {
          q.push(a);
        }
      }
    }
  }
  return numCourses === 0 ? res : [];
};
```

Complexity O(V+E) and O(V+E), where V is the number of verticies and E is the number of edges
