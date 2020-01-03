# 509.Fibonacci Number

## Difficulty:

Easy

## Description

link:
- [https://leetcode.com/problems/fibonacci-number/](https://leetcode.com/problems/fibonacci-number/)

动态规划，那个经典的斐波那契问题。

## Solutions

### cpp

这是常规做法，带备忘（数组记录）的动态规划。

```cpp
class Solution {
public:
    int fib(int N) {
        if(N==0) return 0;
        if(N==1) return 1;

        int F[N+1];
        F[0] = 0;
        F[1] = 1;
        for(int i=2; i<=N; i++) {
            F[i] = F[i-1] + F[i-2];
        }
        return F[N];
    }
};
```

以下是一个更快更巧妙的方法，runtime 100%，memory 100%。

无需设置数组，内存占用更小。利用2个变量 a 和 b，记录前1个数和前2个数。

`a = b - a` 可以得到之前的 b 的值。

```cpp
class Solution {
public:
    int fib(int N) {
        int a=0, b=1;
        if(N<=0) return a;
        for(int i=2; i<=N; i++){
            b = a + b;
            a = b - a;  // previous b
        }
        return b;
    }
};
```