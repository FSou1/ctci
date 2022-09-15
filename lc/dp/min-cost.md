# Min Cost Climbing Stairs

You are given an integer array cost where cost[i] is the cost of ith step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index 0, or the step with index 1.

Return the minimum cost to reach the top of the floor.

```javascript
var minCostClimbingStairs = function(cost) {
    let minCost = [];
    minCost[0] = cost[0];
    minCost[1] = cost[1];
    for(var i = 2; i < cost.length; i++) {
        let plusOne = minCost[i - 1] + cost[i];
        let plusTwo = minCost[i - 2] + cost[i];
        minCost[i] = Math.min(plusOne, plusTwo);
    }
    return Math.min(minCost[cost.length - 1], minCost[cost.length - 2]);
};
```

https://leetcode.com/problems/min-cost-climbing-stairs/?envType=study-plan&id=level-1