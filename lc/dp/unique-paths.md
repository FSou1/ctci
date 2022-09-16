# Unique Paths

Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner. The robot can only move either down or right at any point in time.

```
Input: m = 3, n = 2
Output: 3
Explanation: From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down
```

```javascript
var uniquePaths = function(m, n) {
    let uniquePaths = new Array(m).fill(1).map(() => new Array(n).fill(1));
    uniquePaths[0][0] = 1;
    for(var i = 1; i < m; i++) {
        for(var j = 1; j < n; j++) {
            uniquePaths[i][j] = uniquePaths[i-1][j] + uniquePaths[i][j-1];
        }
    }
    return uniquePaths[m-1][n-1];
};
```

https://leetcode.com/problems/unique-paths/