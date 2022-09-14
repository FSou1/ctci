# Number of islands

Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

```
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
```

```javascript
/**
 * @param {character[][]} grid
 * @return {number}
 */
var numIslands = function(grid) {
    let islands = 0;
    for(var i = 0; i < grid.length; i++) {
        for(var j = 0; j < grid[0].length; j++) {
            let cell = grid[i][j];
            if(cell === '1') {
                islands += 1;
                grid = removeIsland(grid, i, j);
            }
        }
    }
    return islands;
};

var removeIsland = function(grid, i, j) {
    if(grid[i][j] !== '1') {
        return grid;
    }
    
    grid[i][j] = '0';

    if(i >= 1) {
        grid = removeIsland(grid, i - 1, j);
    }
    if((i + 1) < grid.length) {
        grid = removeIsland(grid, i + 1, j);
    }
    if(j >= 1) {
        grid = removeIsland(grid, i, j - 1);
    }
    if((j + 1) < grid[0].length) {
        grid = removeIsland(grid, i, j + 1);
    }
    
    return grid;
}
```