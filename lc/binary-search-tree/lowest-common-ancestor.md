# Lowest Common Ancestor of a Binary Search Tree

Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */

/**
 * @param {TreeNode} root
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */
var lowestCommonAncestor = function(root, p, q) {
    const min = p.val > q.val ? q : p;
    const max = p.val < q.val ? q : p;

    return findLCA(root, min, max);
};

var findLCA = function(node, p, q) {
    if(p.val < node.val && q.val < node.val) {
        return findLCA(node.left, p, q);
    }
    
    if(p.val > node.val && q.val > node.val) {
        return findLCA(node.right, p, q);
    }
    
    return node;
};
```