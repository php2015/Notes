<! --------------  Function类型 ------------------------>

Function对象属性

1、arguments

arguments.length：获取函数实参的个数
arguments.callee：获取函数对象本身的引用
arguments.callee.length：获取函数形参的个数
Javascrip中每个函数都会有一个Arguments对象实例arguments，它引用着函数的实参，可以用数组下标的方式"[]"引用每个实际传入的参数。

示例：
```javascript
function say(a,b,c){
  console.log(arguments.length); //2
  console.log(arguments[0],arguments[1]); //hello world
}
say('hello','world');
```

Function对象方法

1、toString()

功能：将函数体转换成对应的字符串。

2、bind()

功能：创建一个新的函数，在bind()被调用时，这个新函数的this被bind的第一个参数指定，其余的参数将作为新函数的参数供调用时使用。