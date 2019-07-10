# 938. Range Sum of BST

## Difficulty:

Easy

## Description

link:
- [https://leetcode.com/problems/range-sum-of-bst/](https://leetcode.com/problems/range-sum-of-bst/)

## Solutions

### CPP

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
    // root是二叉排序树
    int rangeSumBST(TreeNode* root, int L, int R) {
        if(root != NULL) {
            int val = isRange(root->val, L, R);
            int lval=0, rval=0;
            if(root->left != NULL)
                lval = rangeSumBST(root->left, L, R);
            if(root->right != NULL)
                rval = rangeSumBST(root->right, L, R);
            return val + lval + rval;
        }
        return 0;
    }
    int isRange(int val, int L, int R) {
        if(val >= L && val <= R) return val;
        else return 0;
    }
};
```