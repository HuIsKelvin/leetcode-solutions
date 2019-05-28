# 104. Maximum Depth of Binary Tree

## Description

难度：Easy

link:
- [https://leetcode.com/problems/maximum-depth-of-binary-tree/submissions/](https://leetcode.com/problems/maximum-depth-of-binary-tree/submissions/)

## Solutions

简单地使用递归

### C++

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root == NULL) { return 0; }
        int ldep = maxDepth(root->left);
        int rdep = maxDepth(root->right);
        return ldep > rdep ? (1+ldep) : (1+rdep);
    }
};
```

### Java

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) { return 0; }
        int ldep = maxDepth(root.left);
        int rdep = maxDepth(root.right);
        return ldep > rdep ? (1+ldep) : (1+rdep);
    }
}
```