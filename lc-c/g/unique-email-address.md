# Unique Email Addresses

Given an array of strings emails where we send one email to each emails[i], return the number of different addresses that actually receive mails.

```js
/**
 * @param {string[]} emails
 * @return {number}
 */
var numUniqueEmails = function (emails) {
  const uniqueEmails = new Set()

  for (const email of emails) {
    let localName = []
    for (var i = 0; i < email.length; i++) {
      let currChar = email.charAt(i)

      if (currChar === '+' || currChar === '@') {
        break
      }

      if (currChar === '.') {
        continue
      }

      localName.push(currChar)
    }

    let domainName = []
    for (var j = email.length - 1; j >= 0; j--) {
      let currChar = email.charAt(j)
      if (currChar === '@') {
        break
      }

      domainName.push(currChar)
    }

    const cleanName = localName.join('')
    const cleanDomain = domainName.reverse().join('')

    uniqueEmails.add(`${cleanName}@${cleanDomain}`)
  }

  return uniqueEmails.size
}
```

Complexity O(N * M) and O(N * M)

https://leetcode.com/problems/unique-email-addresses