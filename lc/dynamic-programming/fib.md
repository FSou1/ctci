# Climbing Stairs

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

One can reach i-th step in one of the two ways:
- taking a single step from (i-1)th step
- taking a step of 2 from (i-2)th step

So the total number of ways to reach i-th is equal to sum of ways of reaching (i-1)th step and ways of reaching (i-2)th step.

More details: https://leetcode.com/problems/climbing-stairs/solution/604446

```
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function(n) {
    let dp = [];
    dp[1] = 1;
    dp[2] = 2;
    for(var i = 3; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i-2];
    }
    return dp[n];
};
```