# Count Primes

Given an integer n, return the number of prime numbers that are strictly less than n.

```
Input: n = 10
Output: 4
Explanation: There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
```

## Solution

The basic brute-force solution isn't efficient and fails with exceeding the time limit.

The Approach: Sieve of Eratosthenes is more efficient.

Long story short, we create an array of size `n`, set the elements to `true`, and on each iteration, if the number is not prime, we mark `j += i` as `false`. This algorithm allows us to skip a lot of checks on non-prime numbers.

![](https://leetcode.com/problems/count-primes/Figures/204/img1.png)

![](https://leetcode.com/problems/count-primes/Figures/204/img2.png)

![](https://leetcode.com/problems/count-primes/Figures/204/img3.png)

```
var countPrimes = function(n) {
    let primes = (new Array(n)).fill(true);
    let counter = 0;
    primes[0] = primes[1] = false;
    for(let i = 2; i < n; i++) {
        if(primes[i]) {
            counter += 1;

            for(let j = i*2; j < n; j += i) {
                primes[j] = false;
            }
        }
    }
    return counter;
};
```
