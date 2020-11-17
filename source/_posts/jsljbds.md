title: 计算逻辑表达式
author: kajweb
tags:
  - 携程
  - C++
categories:
  - C++
date: 2020-11-18 03:16:00
---
# 计算逻辑表达式
计算逻辑表达式的值（优先级顺序：`()`>`!`>`&&`>`||`）

## 输入描述
请输入逻辑表达式，表达式由以下字符组成：`T`、`F`、`&&`、`||`、`!`、`(`、`)`、` `。  
>`T`:表示布尔的`true`  
>`F`:表示布尔的`false`

## 输出描述
返回逻辑表达式的结果，油校的结果包括`T`、`F`、`E`  
`T`：表示逻辑表达式的结果为`true`  
`F`：表示逻辑表达式的结果为`false`  
`E`：表示逻辑表达式不正确，不能计算出结果  

## 样例输入
```
T || F && F || F  
! F || T && T
T && F
```

## 样例输出
```
T
T
F
```

## HINT

![upload successful](/images/pasted-0.png

## 代码
> 未测试

```c++
#include<bits/stdc++.h>
using namespace std;

string dealNull( string &str ){
	int finder;
	while( true ){
		// 处理空格
		finder = str.find(" ");
		if( finder == -1 ){
			break;
		}
		str.erase( finder, 1 );
	}
	return str;
}

string deal( string &str ){
	int isError = 0;
	int finder;

	// 处理括号
	int lk = str.find("(");
	int rk =str.rfind(")");
	if( (lk!=-1) xor (rk!=-1) ){
		return "E";
	} else if( (lk!=-1) ) {
		str = str.replace( lk, rk-lk+1, deal(((string)"").assign(str,lk+1,rk-lk-1)) );
	}

	while( true ){
		finder = str.find("!");
		if( finder == -1 ){
			break;
		} else {
			// 处理！
			switch( str[finder+1] ){
				case 'T':
					str[finder+1] = 'F';
					break;
				case 'F':
					str[finder+1] = 'T';
					break;
				case '!':
					str.erase( finder+1, 1 );
				break;
				default:
					isError = 1;
			}
			str.erase( finder, 1 );
			if( isError ) return "E";
		}
	}

	while( true ){
		finder = str.find("&&");
		if( finder == -1 ){
			break;
		} else if( finder<0 || finder==(int)str.length()-1 ) {
			isError = 1;
			break;
		} else {
			if( str[finder-1] == 'T' && str[finder+2] == 'T' ){
				str[finder-1] = 'T';
			} else if( 
				(str[finder-1]=='F'||str[finder-1]=='T') &&
				(str[finder+2]=='T'||str[finder+2]=='F')
			){
				str[finder-1] = 'F';
			} else {
				isError = 1;
			}
		}
		str.erase( finder, 3 );
		if( isError ) return "E";
	}
	
	while( true ){
		finder = str.find("||");
		if( finder == -1 ){
			break;
		} else if( finder<0 || finder==(int)str.length()-1 ) {
			isError = 1;
			break;
		} else {
			if( (str[finder-1]=='T'||str[finder-1]=='F') && (str[finder+2]!='T'||str[finder+2]!='F') ){
				if( 
					(str[finder-1]=='T'&&str[finder+2]=='F') || 
					(str[finder-1]=='F' && str[finder+2]=='T') || 
					(str[finder-1]=='T' && str[finder+2]=='T')
				){
					str[finder-1] = 'T';
				} else {
					str[finder-1] = 'F';
				}
			} else {
				isError = 1;
			}
		}
		str.erase( finder, 3 );
		if( isError ) return "E";
	}
	if( isError ){
		return "E";
	}
	return str;
}

string dealString( string &str ){
	str = dealNull( str );
	str = deal( str );
	return str=="E"||str=="F"||str=="T"?str:"E";
}

int main(){
	string str;
	getline( cin, str );
	string sb = dealString(str);
	cout<<sb<<endl;
}
```