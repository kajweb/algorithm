title: 牛牛切木棒
author: kajweb
tags:
  - 牛客编程巅峰赛
  - ''
categories:
  - 牛客编程巅峰赛S2
date: 2020-11-20 22:06:00
---
> [牛客编程巅峰赛S2第2场](https://ac.nowcoder.com/acm/contest/9223)  
[题目链接](https://ac.nowcoder.com/acm/contest/9223/B)

## 题目描述
牛牛有一根长度为a(`3 \leq a \leq 1e18`)(3≤a≤1e18)的木棒，现在牛牛想将木棒分成一些段（每段木棒长度必须为整数），使得分隔后的木棍中，任意三段都不能构成三角形，牛牛想知道木棒最多被分成几段呢？

## 输入
```
5
```

## 输出
```
3
```

## 说明
```
可以分成1 1 3三段
```

## 题解
```js
/**
 * 
 * @param a long长整型 木棒的长度
 * @return int整型
 */
function stick( a ) {
    // write code here
    if( a<5 )
        return 0;
    let s = [1,1]
    while( true ){
        let next = s[s.length-1] + s[s.length-2];
        if( a>next ){
            s.push( next )
            a -= next;
        } else {
            break;
        }
    }
    return s.length;
}
module.exports = {
    stick : stick
};
```