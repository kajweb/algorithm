title: 今年的第几天
author: kajweb
tags:
  - 明略科技
  - js
categories:
  - js
date: 2020-11-20 14:37:00
---
> 2020-11-20 明略科技集团 2021 校招笔试-前端类 B卷 编程题第一题

## 题目描述
输入年、月、日，计算该天是本年的第几天。

## 输入描述
包括三个整数年（`1≤Y≤3000`）、月（`1≤M≤12`）、日（`1≤D≤31`）  

## 输出描述
输入可能有多组测试数据，对于每一组测试数据，  
输出一个整数，代表Input中的年、月、日对应本年的第几天。  

## 输入
```
1990 9 20
2000 5 1
```

## 输出
```
263
122
```

## 代码实现
```js
while(line=readline()){
	let [years, month, day] = line.split(" ");
	let dateTo = new Date(`${years}-${month}-${day}`);
	let dateForm = new Date(`${years}-1-1`);
	let dateDiff = (dateTo-dateForm) / 1000 / 60 / 60 / 24 + 1;
	print( dateDiff )
}
```