# Implement Trie (Prefix Tree)

A trie (pronounced as "try") or prefix tree is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

```
Explanation
Trie trie = new Trie();
trie.insert("apple");
trie.search("apple");   // return True
trie.search("app");     // return False
trie.startsWith("app"); // return True
trie.insert("app");
trie.search("app");     // return True
```

## Solution

Node

```js
var Node = function () {
  this.children = {};
  this.value = undefined;
};
```

Tree

```js
var Trie = function () {
  this.root = new Node();
};
```

Insert

```js
/**
 * @param {string} word
 * @return {void}
 */
Trie.prototype.insert = function (word) {
  let node = this.root;
  for (let character of word) {
    if (!node.children.hasOwnProperty(character)) {
      node.children[character] = new Node();
    }
    node = node.children[character];
  }
  node.value = word;
};
```

Search

```js
/**
 * @param {string} word
 * @return {boolean}
 */
Trie.prototype.search = function (word) {
  let node = this.root;
  for (let character of word) {
    if (!node.children.hasOwnProperty(character)) {
      return false;
    }
    node = node.children[character];
  }
  return node.value === word;
};
```

Starts with

```js
/**
 * @param {string} prefix
 * @return {boolean}
 */
Trie.prototype.startsWith = function (prefix) {
  let node = this.root;
  for (let character of prefix) {
    if (!node.children.hasOwnProperty(character)) {
      return false;
    }
    node = node.children[character];
  }
  return true;
};
```
