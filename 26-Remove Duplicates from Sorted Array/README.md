# 26.Remove Duplicates from Sorted Array

## Difficulty:

Easy

## Description

link:
- [https://leetcode.com/problems/remove-duplicates-from-sorted-array/](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

## Solutions

### Java

当数组长度为 0 或 1 时，直接返回数组长度；
当数组长度大于1，定义计数器`count`（从1开始）。从`nums[1]`开始遍历，当遇到与前一个数字`post`不同的数，将其与`nums[count]`交换位置。这样操作，就会把重复数字中的单个数向前移到合适位置。

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        // 当数组长度小于等于1
        if(nums.length <= 1) return nums.length;
        // 当数组长度大于1
        int post = nums[0];
        int count = 1;
        for(int i=1; i<nums.length; i++) {
            if(nums[i] != post) {
                post = nums[i];
                // swap
                int tmpInt = nums[count];
                nums[count] = nums[i];
                nums[i] = tmpInt;
                count++;
            }
        }
        return count;
    }
}
```