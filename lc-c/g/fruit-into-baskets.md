# Fruits Into Baskets

Given the integer array fruits, return the maximum number of fruits you can pick.

```js
/**
 * @param {number[]} fruits
 * @return {number}
 */
var totalFruit = function (fruits) {
  let left = 0,
    right = 0
  let max_count = 0
  let basket = new Map()

  for (let right = 0; right < fruits.length; right++) {
    basket.set(fruits[right], (basket.get(fruits[right]) || 0) + 1)

    while (basket.size > 2) {
      basket.set(fruits[left], basket.get(fruits[left]) - 1)
      if (basket.get(fruits[left]) === 0) {
        basket.delete(fruits[left])
      }
      left += 1
    }

    max_count = Math.max(max_count, right - left + 1)
  }

  return max_count
}
```

Complexity is O(N) and O(1).

https://leetcode.com/problems/fruit-into-baskets
