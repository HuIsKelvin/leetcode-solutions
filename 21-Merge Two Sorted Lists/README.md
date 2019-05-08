# 26 Merge Two Sorted Lists

## Description

难度：Easy

link：
- [https://leetcode.com/problems/merge-two-sorted-lists/](https://leetcode.com/problems/merge-two-sorted-lists/)

## Solutions

### C++

有错误，仅作记录。输出结果只有一个节点。
而且在leetcode中使用链表有一个坑

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        // 处理极端情况
        if(l1 == NULL && l2 != NULL) return l2;
        if(l1 != NULL && l2 == NULL) return l1;
        // if(l1 == NULL && l1 == NULL) return;
        
        ListNode *res;
        ListNode *pot = res;
        // 处理头指针
        if(l1->val < l2->val) {
            pot->val = l1->val;
            l1 = l1->next;
        } else {
            pot->val = l2->val;
            l2 = l2->next;
        }
        // 开始遍历
        while(l1 != NULL && l2 != NULL) {
            int tmpval = 0;
            if(l1->val <= l2->val) {
                tmpval = l1->val;
                l1 = l1->next;
            } else {
                tmpval = l2->val;
                l2 = l2->next;
            }
            ListNode *tmpNode;
            if(tmpNode != NULL) {
                tmpNode->val = tmpval;
                tmpNode->next = NULL;   
            }
            if(pot!=NULL)
                pot->next = tmpNode;
            if(pot->next != NULL)
                pot = pot->next;
        }
        // 处理后续
        if(l1 !=NULL) {
            pot->next = l1;
        } else {
            pot->next = l2;
        }
        return res;
    }
};
```

### Java

使用简单粗略的归并算法。

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1 == null && l2 != null) {return l2;}
        if(l1 != null && l2 == null) {return l1;}
        if(l1 == null && l2 == null) {return null;}
        
        ListNode res;
        // 处理头指针
        if(l1.val <= l2.val) {
            res = new ListNode(l1.val);
            l1 = l1.next;
        } else {
            res = new ListNode(l2.val);
            l2 = l2.next;
        }
        ListNode pot = res;
        while(l1 != null && l2 != null) {
            int tmpval = 0;
            if(l1.val <= l2.val) {
                tmpval = l1.val;
                l1 = l1.next;
            } else {
                tmpval = l2.val;
                l2 = l2.next;
            }
            pot.next = new ListNode(tmpval);
            pot = pot.next;
            pot.next = null;
        }
        if(l1 != null) {
            while(l1!=null) {
                pot.next = new ListNode(l1.val);
                l1 = l1.next;
                pot = pot.next;
                pot.next = null;
            }
        }
        if(l2 != null) {
            while(l2 != null) {
                pot.next = new ListNode(l2.val);
                l2 = l2.next;
                pot = pot.next;
                pot.next = null;
            }
        }
        return res;
    } 
}
```