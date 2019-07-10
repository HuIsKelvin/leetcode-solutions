# 100.Same Tree

## Difficulty:

Easy

## Description

link:
- [https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)

## Solutions

### CPP

简单地递归判断两棵树是否相同。

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
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p==NULL && q==NULL) return true;
        if(p==NULL && q!=NULL || p!=NULL && q==NULL) return false;
        
        if(p==q || p->val == q->val) {
            return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
        } else {
            return false;
        }
    }
};
```