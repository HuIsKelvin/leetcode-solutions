# 26.Remove Duplicates from Sorted Array

## Difficulty:

Medium

## Description

link:
- [https://leetcode.com/problems/add-two-numbers/](https://leetcode.com/problems/add-two-numbers/)

## Solutions

### Java

写出来发现和官方solution一样，但不是最优解。

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode fakeResult = new ListNode(0);
        ListNode p = result;
        // 表示进位
        int fwd = 0;
        while(l1!=null || l2!=null) {
            int val1 = (l1==null? 0 : l1.val);
            int val2 = (l2==null? 0 : l2.val);
            int tmpVal = val1 + val2 + fwd;
            fwd = tmpVal / 10;
            p.next = new ListNode(tmpVal % 10);
            p = p.next;
            if(l1!=null) l1 = l1.next;
            if(l2!=null) l2 = l2.next;
        }
        if(fwd != 0) {
            p.next = new ListNode(fwd);
        }
        return fakeResult.next;
    }
}
```