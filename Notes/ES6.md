ECMAScript 6 Study Notes
-----
[ECMAScript 6 Reference Book](https://es6.ruanyifeng.com/)
[toc]

#### 1 let & const
##### 1.1 let
###### 1.1.1 let(basic)
`let`声明的变量只在`let`代码块内有效
**EXAMPLE: `var` vs `let`**
```javascript
var a = [];
for (var i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); // 10
=> 变量i是var命令声明的，在全局范围内都有效，所以全局只有一个变量i
```
```javascript
var a = [];
for (let i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); // 6
=> 变量i是let声明的，当前的i只在本轮循环有效，所以每一次循环的i其实都是一个新的变量
```
```javascript
=> 设置循环变量的那部分是一个父作用域，而循环体内部是一个单独的子作用域
for (let i = 0; i < 3; i++) {
  let i = 'abc';
  console.log(i);
}
// abc
// abc
// abc
```
###### 1.1.2 不存在变量提升
```javascript
//var
console.log(x);//undefined
var x = 0;

//let
=> Reference error
console.log(x);//Reference error
let x = 0;
```
###### 1.1.3 typeof
**在使用变量前，请先声明变量**
- 在变量声明之前使用变量`ReferenceError`
```javascript
typeof x; // ReferenceError
let x;
```
- 未声明的变量`undefined`   
```javascript
typeof undeclared_variable // "undefined"
```
###### 1.1.4 不允许重复声明
`let`不允许在同一个作用域内重复声明同一个变量

##### 1.2 块级作用域
###### 1.2.1 为什么需要块级作用域
1 内层变量可能覆盖外层变量
2 用来计数的循环变量泄漏成全局变量

```javascript
=> 内层变量覆盖外层变量，但是声明前使用，所以`undefined`
var tmp = new Date();

function f() {
  console.log(tmp);
  if (false) {
    var tmp = 'hello world';
  }
}

f(); // undefined
```
###### 1.2.2 ES6的块级作用域 ???
1 允许块级作用域的任意嵌套
2 内层作用域可以定义外层作用域的同名变量
3 **块级作用域的出现，实际上使得获得广泛应用的匿名立即执行函数表达式（匿名 IIFE）不再必要了** **？？？？？？？？？？**

###### 1.2.3 IIFE
立即执行的函数表达式。从名字就可以知道它的作用了。函数同时被创建和调用，你可以这样使用 IIFE：
```javascript
(function() => {})();
//或者
(() => {})();
```
###### 1.2.4 块级作用域与函数声明
- ES5中，函数只能在顶层作用域和函数作用域中声明
- ES6，引入了块级作用域，规定可以在块级作用域中声明函数。
ES6 规定，块级作用域之中，函数声明语句的行为类似于let，在块级作用域之外不可引用。
- 避免在块级作用域内声明函数。如果确实需要，也应该写成函数表达式，而不是函数声明语句。
- ES6 的块级作用域必须有大括号，如果没有大括号，JavaScript 引擎就认为不存在块级作用域。

**EXAMPLE**
```javascript
function f() { console.log('I am outside!'); }

(function () {
  if (false) {
    // 重复声明一次函数f
    function f() { console.log('I am inside!'); }
  }

  f();
}());
```
**ES5**
**JS变量提升机制**
函数声明`function f(){}`会被提升到作用域的最前面。
函数表达式`var ff = function f(){}`不会被提升，运行时赋值，赋值完才能调用（IIFE就不需要赋值了）.
```javascript
//ES5
//if内声明的函数f()会被提升到函数作用域的头部
function f() { console.log('I am outside!'); }
(function () {
  // 重复声明一次函数f
  function f() { console.log('I am inside!');
  if (false) {
     }
  }

  f();//I am inside!
}());
```
**ES6**
块级作用域内声明的函数类似于let，对作用域之外没有影响.
ES6中：
1 允许在块级作用域内声明函数。
2 函数声明类似于var，即会提升到全局作用域或函数作用域的头部。
3 同时，函数声明还会提升到所在的块级作用域的头部。
```javascript
//ES6
function f() { console.log('I am outside!'); }

(function () {
  var f; // undefined
  if (false) {
    // 重复声明一次函数f
    function f() { console.log('I am inside!'); }
  }

  f();// Uncaught TypeError: f is not a function
}());
```

##### 1.3 const
###### 1.3.1 const(basic) ???
- `const`声明一个只读的常量。一旦声明，常量的值就不能改变。
- `const`一旦声明变量，就必须立即初始化，不能留到以后赋值。
- 只在声明所在的块级作用域内有效。
- 命令声明的常量也是不提升
- 不可重复声明

- **常量对象????????????**
常量`foo`储存的是一个地址，这个地址指向一个对象。不可变的只是这个地址，即不能把`foo`指向另一个地址，但对象本身是可变的，所以依然可以为其添加新属性。
```javascript
const foo = {};

// 为 foo 添加一个属性，可以成功
foo.prop = 123;
foo.prop // 123

// 将 foo 指向另一个对象，就会报错
foo = {}; // TypeError: "foo" is read-only
```

##### 1.4 顶层对象的属性
顶层对象，在浏览器环境指的是`window`对象，在 `Node` 指的是`global`对象。`ES5` 之中，顶层对象的属性与全局变量是等价的。
`ES6`中`var`命令和`function`命令声明的全局变量，依旧是顶层对象的属性；另一方面规定，`let`命令、`const`命令、`class`命令声明的全局变量，不属于顶层对象的属性。
```javascript
var a = 1;
// 如果在 Node 的 REPL 环境，可以写成 global.a
// 或者采用通用方法，写成 this.a
window.a // 1

let b = 1;
window.b // undefined
```

##### 1.5 globalThis 对象 ???
全局环境中，`this`会返回顶层对象。但是，`Node` 模块和 **`ES6 `模块中，`this`返回的是当前模块**。
函数里面的`this`，如果函数不是作为对象的方法运行，而是单纯作为函数运行，`this`会指向顶层对象。但是，严格模式下，这时`this`会返回`undefined`。
不管是严格模式，还是普通模式，`new Function('return this')()`，总是会返回全局对象。但是，如果浏览器用了 `CSP（Content Security Policy`，内容安全策略），那么`eval、new Function`这些方法都可能无法使用。

------
#### 2 变量的解构赋值