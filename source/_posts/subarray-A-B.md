title: '[js]判断a是是否为b的子数组'
author: kajweb
tags:
  - js
  - 元戎启行
categories:
  - js
date: 2020-11-04 03:52:00
---
## 题目
```
判断a是是否为b的子数组
```

## 思路
```
遍历数组a，判断每个元素是否在b中出现。  
如果数组a中存在一个元素不在b数组中，则数组a不是数组b的子数组。
```

## 解答
```js
const a = [2, 3, 6];
const b = [1, 2, 3, 4, 5, 6];

function isSubset(a, b) {
    let _isSubset = true;
    a.map(e =>{
        if (b.indexOf(e) == -1) {
            _isSubset = false;
        }
    })
	return _isSubset;
};

console.log(isSubset(a, b))
```