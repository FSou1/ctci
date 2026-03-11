# Simple Bank System

Execute all the valid transactions.

```js
/**
 * @param {number[]} balance
 */
var Bank = function (balance) {
  this.accounts = [...balance]
}

Bank.prototype.isValid = function (account) {
  return account > 0 && account <= this.accounts.length;
}

Bank.prototype.hasBalance = function (account, amount) {
  return this.accounts[account - 1] >= amount;
}

/**
 * @param {number} account1
 * @param {number} account2
 * @param {number} money
 * @return {boolean}
 */
Bank.prototype.transfer = function (account1, account2, money) {
  if (!this.isValid(account1) || !this.isValid(account2)) {
    return false
  }
  if (!this.hasBalance(account1, money)) {
    return false
  }
  this.withdraw(account1, money)
  this.deposit(account2, money)
  return true
}

/**
 * @param {number} account
 * @param {number} money
 * @return {boolean}
 */
Bank.prototype.deposit = function (account, money) {
  if (!this.isValid(account)) {
    return false
  }
  this.accounts[account - 1] += money
  return true
}

/**
 * @param {number} account
 * @param {number} money
 * @return {boolean}
 */
Bank.prototype.withdraw = function (account, money) {
  if (!this.isValid(account)) {
    return false
  }
  if (!this.hasBalance(account, money)) {
    return false
  }
  this.accounts[account - 1] -= money
  return true
}

/**
 * Your Bank object will be instantiated and called as such:
 * var obj = new Bank(balance)
 * var param_1 = obj.transfer(account1,account2,money)
 * var param_2 = obj.deposit(account,money)
 * var param_3 = obj.withdraw(account,money)
 */
```

https://leetcode.com/problems/simple-bank-system/description/
