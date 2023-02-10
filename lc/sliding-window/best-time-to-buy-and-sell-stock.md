# Best Time to Buy and Sell Stock II

You are given an integer array prices where prices[i] is the price of a given stock on the ith day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day.

## Solution

```js
var maxProfit = function (prices) {
  let maxprofit = 0;
  for (let i = 1; i < prices.length; i++) {
    if (prices[i] > prices[i - 1]) {
      maxprofit += prices[i] - prices[i - 1];
    }
  }
  return maxprofit;
};
```

O(N) and O(1).
