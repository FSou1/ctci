# Flood fill

You are also given three integers sr, sc, and color. You should perform a flood fill on the image starting from the pixel image[sr][sc].

```
Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, color = 2
Output: [[2,2,2],[2,2,0],[2,0,1]]
```

```javascript
/**
 * @param {number[][]} image
 * @param {number} sr
 * @param {number} sc
 * @param {number} color
 * @return {number[][]}
 */
var floodFill = function(image, sr, sc, color) {
    const oldColor = image[sr][sc];
    if(color !== oldColor) bfs(image, sr, sc, oldColor, color);
    return image;
};

var bfs = function(image, sr, sc, oldColor, newColor) {
    if(image[sr][sc] == oldColor) {
        image[sr][sc] = newColor;
        if(sr >= 1) bfs(image, sr-1, sc, oldColor, newColor);
        if(sc >= 1) bfs(image, sr, sc-1, oldColor, newColor);
        if((sr + 1) < image.length) bfs(image, sr+1, sc, oldColor, newColor);
        if((sc + 1) < image[0].length) bfs(image, sr, sc+1, oldColor, newColor);
    }
    return image;
};
```