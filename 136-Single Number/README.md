# 136.Single Number

## Difficulty:

Easy

## Description

Link:
- [https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)
- [https://leetcode-cn.com/problems/single-number/description](https://leetcode-cn.com/problems/single-number/description)

## Solutions

### Java

#### 解法1

实在想不到，看的答案。
标准答案，用异或运算符`^`来做。（我太菜了吧）

```java
class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for(int tmp : nums) {
            result ^= tmp;
        }
        return result;
    }
}
```

####解法2

暴力解法，多重遍历.
Runtime 低得可怜。

```
Runtime: 113 ms, faster than 5.02% of Java online submissions for Single Number.
Memory Usage: 38.3 MB, less than 90.08% of Java online submissions for Single Number.
```

```java
class Solution {
    public int singleNumber(int[] nums) {
        for(int i = 0; i < nums.length; i++) {
            boolean flag = true;
            for(int j = 0; j < i; j++) {
                if(nums[i] == nums[j]) flag = false;
            }
            for(int j = i + 1; j < nums.length; j++) {
                if(nums[i] == nums[j]) flag = false;
            }
            if(flag == true) return nums[i];
        }
        return nums[0];
    }
}
```

### c++

与`java`解法一样。

```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int result = 0;
        for(int i = 0; i < nums.size(); i++) {
            result ^= nums[i];
        }
        return result;
    }
};
```