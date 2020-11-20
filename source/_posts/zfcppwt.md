title: 字符串匹配问题
author: kajweb
tags:
  - 明略科技
  - js
categories:
  - js
date: 2020-11-20 14:43:00
---
> 2020-11-20 明略科技集团 2021 校招笔试-前端类 B卷 编程题第二题

[牛客网原题：CD136](https://www.nowcoder.com/questionTerminal/7ab95c2bbfc941a89c13c78128914e14)

## 题目描述
对于字符串str，其中绝对不含有字符`.`和`*`。再给定字符串exp，其中可以含有`.`或``*`，`*`字符不能是exp的首字符，并且任意两个`*`字符不相邻。exp中的`.`代表任何一个字符，exp中的`*`表示`*`的前一个字符可以有0个或者多个。请写一个函数，判断str是否能被exp匹配(注意：输入的数据不保证合法，但只含小写字母和`.`和`*`)。

## 输入
```
"abc", "abc"
```

## 输出
```
true
```

## 备注
```
1≤|str|, |exp|≤300
```

## 实现
```js
function canMatch( str, exp ){
	// 异常筛选
	if( str.indexOf("*") != -1 || str.indexOf("*") != -1 || exp.indexOf("*") == 0 || exp.indexOf("**") != -1 )
		return false;
	while( str.length && exp.length ){
		let currExp = exp[0];	// 当前匹配的字符（首个）
		let nextIsX  = false;	// 记录下一个是否为*
		if( exp.length>1 && exp[1] == "*" )
			nextIsX = true;
		// 将.重新定义为字符串首个字符
		if( currExp == '.' )
			currExp = str[0];
		if( nextIsX ){
			// 如果接下来带星号，首先删除字符串前面相同的值，然后删除exp前面相同的值/*
			while( str[0] == currExp ){
				str=str.substr( 1 );
			}
			while( exp[0] == currExp || exp[0] == "*" ){
				exp=exp.substr( 1 );
			}
		} else if( currExp == str[0] ){
			// 如果只是单字符，且不带exp。直接删除首个字符
			str=str.substr( 1 );
			exp=exp.substr( 1 );
		} else {
			// 如果第一个字符不相同，且第二个字符不是*
			return false;
		}
	}
	return str.length && exp.length ? false : true; 
}

console.log( canMatch( "aaaabc", "a*abc" ) )

```