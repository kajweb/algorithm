title: 热心的牛牛
author: kajweb
tags:
  - 牛客编程巅峰赛
  - ''
categories:
  - 牛客编程巅峰赛S2
date: 2020-11-20 22:00:00
---
> [牛客编程巅峰赛S2第2场](https://ac.nowcoder.com/acm/contest/9223)  
[题目链接](https://ac.nowcoder.com/acm/contest/9223/A)

## 题目描述
牛牛是个非常热心的人，所以他有很多的朋友。这一天牛牛跟他的n个朋友一起出去玩，在出门前牛牛的妈妈给了牛牛k块糖果，牛牛决定把这些糖果的一部分分享给他的朋友们。由于牛牛非常热心，所以他希望他的每一个朋友分到的糖果数量都比牛牛要多（严格意义的多，不能相等）。牛牛想知道他最多能吃到多少糖果？

## 输入
```
2,10
```

## 输出
```
2
```

## 说明
牛牛可以分给他的两个朋友各4个糖果，这样他能吃到2个糖果，这样能保证他的每个朋友的糖果数都比他多，不存在牛牛能吃到3个或者以上糖果的情况

## 输入
```
3,11
```

## 输出
```
2
```

## 说明
牛牛可以分给他的3个朋友各3个糖果，这样他能吃到2个糖果，这样能保证他的每个朋友的糖果数都比他多，不存在牛牛能吃到3个或者以上糖果的情况

## 备注

对于百分之30的数据：`1\leq n\leq 100`,`n\leq k\leq 1001≤n≤100,n≤k≤100`

对于百分之100的数据：1\leq n\leq 1e18`,`n\leq k\leq 1e181≤n≤1e18,n≤k≤1e18`
`
函数有两个long long型参数

第一个参数代表题目中的n

第二个参数代表题目中的k

## 题解
```c++
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     * 返回牛牛能吃到的最多糖果数
     * @param n long长整型 
     * @param k long长整型 
     * @return long长整型
     */
    long long Maximumcandies(long long n, long long k) {
        // write code here
        return (k-n) / (n+1);
    }
};
```

## 备注
这题使用JS实现的话，会因为JS的`int`的`Number.MAX_SAFE_INTEGER`为`9007199254740991`（`Math.pow(2,53)-1`）。  
需要使用`BigInt`，或大数处理类。  
但是在实际评测中，使用BigInt只能`AC 90%`。 具体原因不详。  
```js
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 * 返回牛牛能吃到的最多糖果数
 * @param n long长整型 
 * @param k long长整型 
 * @return long长整型
 */
function Maximumcandies( n ,  k ) {
    return parseInt((BigInt(k)-BigInt(n)) / (BigInt(n)+1n));
}
module.exports = {
    Maximumcandies : Maximumcandies
};
```