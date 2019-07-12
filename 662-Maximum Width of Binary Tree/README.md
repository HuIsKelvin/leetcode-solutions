# 662.Maximum Width of Binary Tree

## Difficulty:

Medium

## Description

link:
- [https://leetcode.com/problems/maximum-width-of-binary-tree/](https://leetcode.com/problems/maximum-width-of-binary-tree/)

## Solutions

### Java

（还是看了答案才做的，太菜了 /(ㄒoㄒ)/~~）

利用广度优先遍历的思想，逐层遍历这棵树。

新建了一个类 `DetailNode` 来记录每个节点的层级 `level` 和其在完全二叉树中的位置 `index` ，便于计算。

```java
/**
 * 这个判断，是为了及时更新每一层中最左边节点的位置，以此来计算该层的宽度。
 */
if(node.level != curLevel) {
    curLevel = node.level;
    curLeft = node.index;
}
```

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
    public int widthOfBinaryTree(TreeNode root) {
        if(root==null) { return 0; }
        
        Queue<DetailNode> nodeQue = new LinkedList();
        nodeQue.add(new DetailNode(root, 1, 0));
        int curLevel = 0, curLeft = 0, res = 0;
        
        while(!nodeQue.isEmpty()) {
            DetailNode node = nodeQue.poll();
            if(node != null) {
                if(node.node.left != null)
                    nodeQue.add(new DetailNode(node.node.left, node.level+1, node.index*2));
                if(node.node.right != null)
                    nodeQue.add(new DetailNode(node.node.right, node.level+1, node.index*2+1));
                if(node.level != curLevel) {
                    curLevel = node.level;
                    curLeft = node.index;
                }
                res = (res < node.index - curLeft + 1) ? (node.index - curLeft + 1) : res;
            }
        }
        return res;
    }
}

class DetailNode {
    TreeNode node;
    int level, index;
    DetailNode(TreeNode node, int level, int index) {
        this.node = node;
        this.level = level;
        this.index = index;
    }
}
```