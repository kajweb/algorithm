title: 十进制二进制
author: kajweb
tags:
  - C
categories:
  - C
date: 2020-11-18 03:35:00
---
## 题目描述
拟将任意给定的正整数n转换成对应的二进制数的过程：对于输入的任意正整数n，输出若干行“shang:* yu:*”的形式，表示其转换过程。

## 输入描述
输入正整数n。

## 输出描述
输出其转为二进制的过程(具体见样例)。

## 示例输入
```
13
```

## 示例输出
```
shang:6 yu:1
shang:3 yu:0
shang:1 yu:1
shang:0 yu:1
```

## HINT
```c
#include<stdio.h>

int main(){
    int n;
    scanf( "%d", &n );
    while( n!=1 ){
        int mod = n % 2;
        if( mod == 1 ){
            n = n-1;
        }
        n /= 2;
        printf( "shang:%d yu:%d\n", n, mod );
    }
    printf( "shang:0 yu:1\n" );
    return 0;
}
```

[题目链接](https://ac.nowcoder.com/acm/problem/15482)