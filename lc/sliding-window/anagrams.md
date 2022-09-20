# Find All Anagrams in a String

Given two strings s and p, return an array of all the start indices of p's anagrams in s.

```
Input: s = "cbaebabacd", p = "abc"
Output: [0,6]
Explanation:
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
```

Solution:

```javascript
/**
 * @param {string} s
 * @param {string} p
 * @return {number[]}
 */
var findAnagrams = function(s, p) {
    let ns = s.length,
        np = p.length;
    if (ns < np)
        return [];

    let pCount = new Array(26).fill(0),
        sCount = new Array(26).fill(0);

    for (let i = 0; i < p.length; i++) {
      pCount[p.charCodeAt(i) - 97]++;
    }

    let output = [];

    // sliding window on the string s
    for (let i = 0; i < ns; ++i) {
      // add one more letter 
      // on the right side of the window
      sCount[s.charCodeAt(i) - 97]++;

      // remove one letter 
      // from the left side of the window
      if (i >= np) {
        sCount[s.charCodeAt(i - np) - 97]--;
      }

      // compare array in the sliding window
      // with the reference array
      if (equal(pCount, sCount)) {
        output.push(i - np + 1);
      }
    }

    return output;
};

var equal = function(a, b) {
    return JSON.stringify(a) === JSON.stringify(b);
}
```

https://leetcode.com/problems/find-all-anagrams-in-a-string/solution/