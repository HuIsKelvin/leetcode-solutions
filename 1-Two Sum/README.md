# Two sum

## Description

难度：Easy

找到两数之和为目标值的配对，只有唯一解。

解释：

```
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

例子：
```
// input
[3,2,4]
6

// output
[0,1]
```

Link:
- [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)
- [https://leetcode-cn.com/problems/two-sum/description](https://leetcode-cn.com/problems/two-sum/description)

## Solutions

### Java

对数组排序得到`tmpArr`，用索引`i`、`j`分别指向数组头尾元素；
若`tmpArr[i] + tmpArr[j] > target`，则`j--`;
若`tmpArr[i] + tmpArr[j] < target`，则`i++`;
找到两个元素后，再回原数组找到对应索引。

```java
import java.util.Arrays;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] tmparr = new int[nums.length];
        for(int i=0; i< nums.length; i++) {
            tmparr[i] = nums[i];
        }
        // sort the tmp arr
        Arrays.sort(tmparr);
        int[] res = new int[2];
        int i = 0;
        int j = tmparr.length -1;
        while(i < j) {
            if(tmparr[i] + tmparr[j] == target) {
                res[0] = indexOf(tmparr[i], nums);
                res[1] = indexOfLast(tmparr[j], nums);
                break;
            } else if(tmparr[i] + tmparr[j] > target) {
                j--;
            } else if(tmparr[i] + tmparr[j] < target) {
                i++;
            }
        }
        return res;
    }
    
    private int indexOf(int el, int[] arr) {
        int i = 0;
        for(; i<arr.length; i++) {
            if(el == arr[i]) return i;
        }
        return -1;
    }
    private int indexOfLast(int el, int[] arr) {
        int i = arr.length-1;
        for(; i>=0; i--) {
            if(el == arr[i]) return i;
        }
        return -1;
    }
}
```

#### 缺点

拷贝了一份数组，占多了内存。要回原数组找索引，时间复杂度高了。

### c++