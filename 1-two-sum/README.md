# Two sum

## description

[link to](https://leetcode.com/problems/two-sum/)

## solutions

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