# Roman to Integer

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Given a roman numeral, convert it to an integer.

```
Input: s = "III"
Output: 3
Explanation: III = 3.
```

```
/**
 * @param {string} s
 * @return {number}
 */
var romanToInt = function(s) {
    let result = 0;
    for(let i = s.length - 1; i >= 0; i--) {
        let current = getNumber(s[i]),
            prev = getNumber(s[i + 1]);
        if(current >= prev) {
            result += current;
        } else {
            result -= current;
        }
    }
    return result;
};

function getNumber(roman) {
    if(roman === 'I') return 1;
    if(roman === 'V') return 5;
    if(roman === 'X') return 10;
    if(roman === 'L') return 50;
    if(roman === 'C') return 100;
    if(roman === 'D') return 500;
    if(roman === 'M') return 1000;
    return 0;
}
```

O(N)/O(1) and O(1).
