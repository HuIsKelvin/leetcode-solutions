# 17.ZigZag Conversion

## Difficulty:

Medium

## Description

link:
- [https://leetcode.com/problems/zigzag-conversion/](https://leetcode.com/problems/zigzag-conversion/)

## Solutions

### Java

这是看了别人做法写的...也是最直观的做法。

```java
class Solution {
    public String convert(String s, int numRows) {
        String resultStr = "";
        if(s==null || s.length()==0 || numRows==0) { return resultStr; }
        // preparetion
        int length = s.length();
        String[] store = new String[numRows];
        for(int i = 0; i < numRows; i++) {
            store[i] = "";
        }
        // begin zigzag
        int idx = 0;
        while(idx < length) {
            for(int i = 0; i < numRows && idx < length; i++) {
                store[i] += s.charAt(idx);
                idx++;
            }
            for(int i = numRows-2; i>=1 && idx < length; i--) {
                store[i] += s.charAt(idx);
                idx++;
            }
        }
        // generate result
        for(int i = 0; i < store.length; i++) {
            resultStr += store[i];
        }
        return resultStr;
    }
}
```