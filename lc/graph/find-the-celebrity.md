# Find the Celebrity

Suppose you are at a party with n people labeled from 0 to n - 1 and among them, there may exist one celebrity. The definition of a celebrity is that all the other n - 1 people know the celebrity, but the celebrity does not know any of them.

You are given a helper function bool knows(a, b) that tells you whether a knows b. Implement a function int findCelebrity(n). There will be exactly one celebrity if they are at the party.

Return the celebrity's label if there is a celebrity at the party. If there is no celebrity, return -1.

## Solution

![alt text](https://assets.leetcode.com/uploads/2019/10/20/hint_find_celebrity.png)

```js
var solution = function (knows) {
  /**
   * @param {integer} n Total people
   * @return {integer} The celebrity
   */
  return function (n) {
    let potential_celebrity = 0;
    let next = 1;
    do {
      if (knows(potential_celebrity, next)) {
        potential_celebrity = next;
      }
    } while (next++ < n);

    for (let i = 0; i < n; i++) {
      if (i === potential_celebrity) continue;
      if (!knows(i, potential_celebrity) || knows(potential_celebrity, i)) {
        return -1;
      }
    }

    return potential_celebrity;
  };
};
```

O(N) and O(1).
