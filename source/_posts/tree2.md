title: Tree II
author: kajweb
tags:
  - 牛客编程巅峰赛
  - 牛客编程巅峰赛S2第二场
  - ''
categories:
  - 牛客编程巅峰赛S2
date: 2020-11-20 22:08:00
---
> [牛客编程巅峰赛S2第2场](https://ac.nowcoder.com/acm/contest/9223)  
[题目链接](https://ac.nowcoder.com/acm/contest/9223/C)

## 题目
系统中有一棵n个点的完全k叉树，现给出它的BFS层序遍历序列ai（即从根节点开始，每一层从左向右遍历），请你还原这棵树，并返回加密后的答案。
答案加密方法：所有边两个端点异或的和，即
![upload successful](/images/pasted-1.png)，其中
![upload successful](/images/pasted-2.png)为一条树上的边。

下面给出完全二叉树的定义：若设二叉树的深度为k，除第 k 层外，其它各层 (1～k-1) 的结点数都达到最大个数，第k层所有的结点都**连续集中在最左边**。
**请你根据这个定义进行适度推广，得到完全k叉树的含义。**

## 输入
```
2,[1,2,3,4,5]
```

## 输出
```
18
```

## 说明
树边为(1, 2), (1, 3), (2, 4), (2, 5)，加密过程为(1^2)+(1^3)+(2^4)+(2^5)，答案为18。

样例1构成的完全二叉树为：
![](https://uploadfiles.nowcoder.com/images/20200527/329682_1590557746727_4A47A0DB6E60853DEDFCFDF08A5CA249)

## 输入2
```
3,[1,2,3,4,5]
```

## 输出2
```
17
```

## 说明2
树边为(1, 2), (1, 3), (1, 4), (2, 5)，加密过程为(1^2)+(1^3)+(1^4)+(2^5)，答案为17。

样例2构成的完全三叉树为：

![](https://uploadfiles.nowcoder.com/images/20200528/329682_1590638604746_10FB15C77258A991B0028080A64FB42D)

## 备注
![upload successful](/images/pasted-3.png)

## 题解
```js
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 * 
 * @param k int整型 表示完全k叉树的叉数k
 * @param a int整型一维数组 表示这棵完全k叉树的Bfs遍历序列的结点编号
 * @return long长整型
 */
function tree2( k ,  a ) {
    // write code here
    let arr = a.shift( 1 );
    let maxLen = k;
    while( a.length ){
        if( a.length>maxLen ){
            arr.push( a.splice( 0, maxLen ) );
            k = k * k;
        } else {
            arr.push( a.splice() );
        }
    }
    let sum = 0;
    arr.map((e,i)=>{
        if( i==0 )
            return true;
        e.map((item,itemIndex)=>{
            let p = 
        })
    })
}
module.exports = {
    tree2 : tree2
};
```
