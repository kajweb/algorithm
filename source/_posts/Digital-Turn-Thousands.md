title: '[js]数字转字符串千分位'
author: kajweb
tags:
  - js
  - 元戎启行
categories:
  - js
date: 2020-11-04 04:00:00
---
## 题目
```
数字转字符串千分位
```

## 输入
```
1000000.01
```

## 输出
```
1,000,000.01
```

## 回答

### 回答1
```js
function a( _num ){
    _str = _num.toString();
    let _arr = _str.split(".");
    let _newStr = "";
    var t = 0;
    for( let i=_arr[0].length-1;i>=0;i-- ){
        if( t==2 ){
            _newStr = `,${_arr[0][i]}${_newStr}`;
            t = 0;
        } else {
            _newStr = `${_arr[0][i]}${_newStr}`;
            t++;
        }
    }

    // 处理前置的“ , ”
    _newStr = _newStr.replace( /^,?(.*?),?$/g, "$1" );
  
    // 拼接整数部分
    if( _arr[1] ){
        return `${_newStr}.${_arr[1]}`;
    } else {
        return `${_newStr}`;
    }
}
console.log( a( 1000000.01 ) )
```

### 回答2
```js
function b( _num ){
      return _num.toString().replace( /\d{1,3}(?=(\d{3})+)(?=.\d*)/g, "$&," )
}
console.log( b( 1000000.01 ) )
```

### 回答3
```js
function c( _num ){
      return _num.toLocaleString()
}
console.log( c( 1000000.01 ) )
```