title: 实现32进制加法计数器
author: kajweb
tags:
  - js
categories:
  - js
  - ''
  - ''
date: 2020-11-18 13:18:00
---
## 题目
32进制数相加

```js
// fromCharCode() 可接受一个指定的 Unicode 值，然后返回一个字符串
// charCodeAt() 方法可返回指定位置的字符的 Unicode 编码。这个返回值是 0 - 65535 之间的整数。

function hexPlus36( string1, string2 ){
	let currentIndex = 0;
	let start = "0";
	let end = "Z";
	let isAdd = false;	// 进位标志符
	let startCharCode = start.charCodeAt();
	let endCharCode = end.charCodeAt();
	let sum = [];	//总和
	let Lenstring1 = string1.length;
	let Lenstring2 = string2.length;
	while( Lenstring1>currentIndex ||  Lenstring2>currentIndex ){
		// 对两位进行预处理，屏蔽[9-a]中间的字符
		let addA = startCharCode;
		if( Lenstring1>currentIndex ){
			let currentCharCode = string1.charCodeAt(Lenstring1-currentIndex-1);
			if( currentCharCode >= startCharCode+9 ){
				addA = currentCharCode - "a".charCodeAt() + startCharCode + 10;
			} else {
				addA = currentCharCode;
			}
		}
		let addB = startCharCode;
		if( Lenstring2>currentIndex ){
			let currentCharCode = string2.charCodeAt(Lenstring2-currentIndex-1);
			if( currentCharCode >= startCharCode+9 ){
				addB = currentCharCode - "a".charCodeAt() + startCharCode + 10;
			} else {
				addB = currentCharCode;
			}
		}

		// 进行加法
		let sumCharCode = (isAdd&&1) + addA + addB - startCharCode;
		if( sumCharCode >= startCharCode + 36 ){
			sumCharCode -= 36;
			isAdd = true;
		}
		// 回退屏蔽
		if( parseInt(sumCharCode) > startCharCode+9 ){
			sumCharCode +=  "a".charCodeAt() - startCharCode - 10;
		}
		sum.unshift( String.fromCharCode(sumCharCode) );
		currentIndex++;
	}
	if( isAdd )
		sum.unshift( String.fromCharCode(startCharCode+1) );
	return sum.join("");
}

let result = hexPlus36("1","1");
console.log( result );
```