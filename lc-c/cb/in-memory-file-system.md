# Design In-Memory File System

Implement the FileSystem class.

```js
var Dir = function () {
  this.dirs = {}
  this.files = {}
}

var FileSystem = function () {
  this.root = new Dir()
}

/**
 * @param {string} path
 * @return {string[]}
 */
FileSystem.prototype.ls = function (path) {
  const dirs = Object.keys(this.root.dirs)
  const files = Object.keys(this.root.files)
  let inner = []
  let current = this.root

  if (path !== '/') {
    let isFile = false
    let isFolder = false
    const parts = path.replace('/', '').split('/')
    for (var part of parts) {
      if (current.dirs.hasOwnProperty(part)) {
        current = current.dirs[part]
        isFolder = true
      } else {
        if (current.files.hasOwnProperty(part)) {
          isFile = true
        }
      }
    }

    if (isFile) {
      return [parts[parts.length - 1]]
    }

    if (isFolder) {
      return []
        .concat(Object.keys(current.dirs), Object.keys(current.files))
        .sort()
    }
  }

  return [].concat(dirs, files, inner).sort()
}

/**
 * @param {string} path
 * @return {void}
 */
FileSystem.prototype.mkdir = function (path) {
  let current = this.root
  const parts = path.replace('/', '').split('/')
  for (var part of parts) {
    if (!current.dirs.hasOwnProperty(part)) {
      current.dirs[part] = new Dir()
    }
    current = current.dirs[part]
  }
}

/**
 * @param {string} filePath
 * @param {string} content
 * @return {void}
 */
FileSystem.prototype.addContentToFile = function (filePath, content) {
  let current = this.root
  const parts = filePath.replace('/', '').split('/')
  const folders = parts.splice(0, parts.length - 1)
  const fileName = parts[parts.length - 1]
  for (var part of folders) {
    if (!current.dirs.hasOwnProperty(part)) {
      current.dirs[part] = new Dir()
    }
    current = current.dirs[part]
  }
  if (current.files.hasOwnProperty(fileName)) {
    current.files[fileName] += content
  } else {
    current.files[fileName] = content
  }
}

/**
 * @param {string} filePath
 * @return {string}
 */
FileSystem.prototype.readContentFromFile = function (filePath) {
  let current = this.root
  const parts = filePath.replace('/', '').split('/')
  const folders = parts.splice(0, parts.length - 1)
  const fileName = parts[parts.length - 1]
  for (var part of folders) {
    if (!current.dirs.hasOwnProperty(part)) {
      current.dirs[part] = new Dir()
    }
    current = current.dirs[part]
  }
  return current.files[fileName]
}

/**
 * Your FileSystem object will be instantiated and called as such:
 * var obj = new FileSystem()
 * var param_1 = obj.ls(path)
 * obj.mkdir(path)
 * obj.addContentToFile(filePath,content)
 * var param_4 = obj.readContentFromFile(filePath)
 */
```

https://leetcode.com/problems/design-in-memory-file-system
