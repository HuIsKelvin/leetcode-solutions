# 13. Roman To Integer

## Difficulty:

Medium

## Description

link:
- [https://leetcode.com/problems/roman-to-integer/](https://leetcode.com/problems/roman-to-integer/)

## Solutions

### C++

对字符串从后往前遍历，若当前字符小于后一个字符，sum减去当前字符；若大于，则加当前字符。

```c++
class Solution {
public:
  int romanToInt(string s) {
    int res = 0;
    int tmp = 0;
    for(int i = s.length()-1; i>=0; i--) {
      int now = match(s[i]);
      if(now < tmp) { res -=now; } 
      else { res +=now; } 
      tmp=now; 
    } 
    return res; 
  };
  int match(char ch) { 
    switch(ch){ 
      case 'I' :
        return 1; break; 
      case 'V' : 
        return 5; break; 
      case 'X' : 
        return 10; break; 
      case 'L' : 
        return 50; break; 
      case 'C' :
        return 100; break; 
      case 'D' : 
        return 500; break; 
      case 'M' : return 1000; break; 
      default: 
        return 0; 
    } 
  } 
}; 
```