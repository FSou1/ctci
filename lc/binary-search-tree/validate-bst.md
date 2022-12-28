# Validate binary search tree

Given the root of a binary tree, determine if it is a valid binary search tree (BST).

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isValidBST = function(root) {
    return isNodeValid(root, []);
};

var isNodeValid = function(node, conditions) {
    let conditionsValid = true;
    if(conditions) {
        conditionsValid = conditions.every(func => func(node.val));
        if(!conditionsValid) {
            return false;
        }
    }
    
    let leftIsValid = true;
    if(node.left) {
        leftIsValid = isNodeValid(node.left, [...conditions].concat((v) => v < node.val));
        if(!leftIsValid) {
            return false;
        }
    }
    
    let rightIsValid = true;
    if(node.right) {
        rightIsValid = isNodeValid(node.right, [...conditions].concat((v) => v > node.val));
        if(!rightIsValid) {
            return false;
        }
    }
    
    return true;
};
```