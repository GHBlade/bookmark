# JS进阶

#### [ECMAScript 6](http://es6.ruanyifeng.com/) (ES6/ECMAScript2015) 是javascript语言的下一代标准
> (ps:Babel是一个广泛使用的ES6转码器，可以将ES6代码转为ES5代码)
> ES6最常用的语法：let, const, class, extends, super, arrow functions, template string, destructuring, default, rest arguments

####let,const
> 使用var, ES5只有全局作用域和函数作用域，没有块级作用域.
> let为JavaScript新增了块级作用域.
####class, extends, super

####arrow function
> function(i){ return i + 1; } //ES5
> (i) => i + 1 //ES6

```
function(x, y) {
    x++;
    y--;
    return x + y;
}
(x, y) => {x++; y--; return x+y}
```
####template string
```
$("#result").append(`
  There are <b>${basket.count}</b>items
   in your basket, <em>${basket.onSale}</em>
  are on sale!
`);
```
> 用反引号（\`）来标识起始，用${}来引用变量，而且所有的空格和缩进都会被保留在输出之中

####destructuring
> ES6允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构（Destructuring）
```
let cat = 'ken'
let dog = 'lili'
let zoo = {cat, dog}
console.log(zoo)  //Object {cat: "ken", dog: "lili"}
```
```
let dog = {type: 'animal', many: 2}
let { type, many} = dog
console.log(type, many)   //animal 2
```
####default, rest
> default很简单，意思就是默认值。 如调用animal()方法时忘了传参数，传统的做法就是加上这一句type = type || 'cat' 来指定默认值
```
function animal(type){
    type = type || 'cat'  
    console.log(type)
}
animal()
```
> ES6我们直接这么写
```
function animal(type = 'cat'){
    console.log(type)
}
animal()
```
> rest语法
```
function animals(...types){
    console.log(types)
}
animals('cat', 'dog', 'fish') //["cat", "dog", "fish"]
```

####import export

#### JS进阶
* [基本类型 引用类型 简单赋值 对象引用](https://segmentfault.com/a/1190000002789651)
