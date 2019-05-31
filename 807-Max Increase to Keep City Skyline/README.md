# 807. Max Increase to Keep City Skyline

## Difficulty:

Medium

## Description

link:
- [https://leetcode.com/problems/max-increase-to-keep-city-skyline/](https://leetcode.com/problems/max-increase-to-keep-city-skyline/)

## Solutions

### Java

完整遍历两次矩阵，感觉还能再优化，减少遍历次数。

```java
class Solution {
    public int maxIncreaseKeepingSkyline(int[][] grid) {
        // 处理极端情况
        if(grid == null || grid.length == 0 || (grid.length >= 1 && grid[0].length == 0)) {
            return 0;
        } else if(grid.length == 1 && grid[0].length == 1) {
            return 0;
        }
        int resultSum = 0;
        int[] fromTop = new int[grid[0].length];
        int[] fromLeft = new int[grid.length];
        // 查找行列最大值
        for(int i = 0; i < grid.length; i++) {
            for(int j = 0; j < grid[0].length; j++) {
                // 查找从上往下看的，最大值
                if(fromTop[j] < grid[i][j]) {
                    fromTop[j] = grid[i][j];
                }
                // 查找从左往右看，最大值
                if(fromLeft[i] < grid[i][j]) {
                    fromLeft[i] = grid[i][j];
                }
            }
        }
        for(int i = 0; i < grid.length; i++) {
            for(int j = 0; j < grid[0].length; j++) {
                int tmpMax = (fromTop[j] <= fromLeft[i] ? fromTop[j] : fromLeft[i]);
                resultSum += (tmpMax - grid[i][j]);
            }
        }
        return resultSum;
    }
}
```