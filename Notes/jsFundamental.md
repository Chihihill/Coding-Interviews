[toc]

----
##### 1.逻辑运算符

1. 或 ||
与 &&
非 ！

2. 条件（三元）运算符
```javascript
    variableName = (condition) ? value1:value2

    if(condotion){
        variableName = value1
    }else{
        variablename = value2
    }
```
---
##### 2.switch
默认的 `case `不必是 `switch` 代码块中最后一个` case`,可以放在开头。
如果` default` 不是 `switch` 代码块中最后一个` case`，请记得用 `break` 结束默认 `case`。
- 如果多种 case 匹配一个 case 值，则选择第一个 case。
- 如果未找到匹配的 case，程序将继续使用默认 label。
- 如果未找到默认 label，程序将继续 switch 后的语句。
- Switch case 使用严格比较（===）。值必须与要匹配的类型相同。只有操作数属于同一类型时，严格比较才能为 true。

```javascript
    //语法
    switch(表达式) {
        case n:
            代码块
            break;//跳出代码块
        case n:
            代码块
            break;
        default: //关键词规定不存在 case 匹配时所运行的代码
            默认代码块
    } 
    //
    switch (new Date().getDay()) {
        //getDay()返回0-Sunday, 1-Monday....
    case 0:
        day = "星期天";
        break;
    case 1:
        day = "星期一";
         break;
    case 2:
        day = "星期二";
         break;
    case 3:
        day = "星期三";
         break;
    case 4:
        day = "星期四";
         break;
    case 5:
        day = "星期五";
         break;
    case 6:
        day = "星期六"; //最后一个case无需中断，自动结束
} 
```
- 不同的`case`使用相同的代码:
```javascript
    case0:
    case1:
        text = "今天是周末~";
        break;
```
---
##### 3.循环
1. `for `- 多次遍历代码块

2. `for/in `- 遍历对象属性
```javascript
    var person = {fname:"Bill", lname:"Gates", age:62}; 

    var text = "";
    var x;
    for (x in person) {
        text += person[x];
    }
```
3. `while` - 当指定条件为 `true `时循环一段代码块
`while` 循环会一直循环代码块，只要指定的条件为 true。
```javascript
    var i = 0;
    var text = "";
    while (i < 10) {
        text += "数字是 " + i;
        i++;
    }
```
4. `do/while` - 当指定条件为 `true` 时循环一段代码块
在检查条件是否为真之前，这种循环会执行一次代码块，然后只要条件为真就会重复循环。
不要忘记对条件中所用变量进行递增，否则循环永不会结束！
```javascript
    var i = 0;
    do{
        text = text + "the number is " + i;
        i++;
    }
    while(i<10);
```
---
##### 4.break vs continue
`break`用于跳出循环
```javascript
    for(var i = 0;i < 10； i++){
        if(i==3){break}
        text += "数字是 " + i + "<br>";
    }
```
`continue`用于跳过/中断一个迭代
```javascript
    for(var i = 0;i < 10； i++){
        if(i==3){continue}
        text += "数字是 " + i + "<br>";
    }
```
- 标签`label`
`continue` 语句（不论有无标签引用）只能用于跳过一个迭代。
`break` 语句，如果没有标签引用，只能用于跳出一个循环或一个 switch。如果有标签引用，则 break 语句可用于跳出任意代码块:
```javascript
    label: //标记语句，将label：置于被标记语句之前
    statements
////
    break labelname;
    continue labelname;
////break跳出多个代码块
    var  cars = ["BMW", "Volvo", "Saab", "Ford"];
    list: {//label
        text += cars[0] + "<br>"; 
        text += cars[1] + "<br>"; 
        text += cars[2] + "<br>"; 
        break list;
        text += cars[3] + "<br>"; 
        text += cars[4] + "<br>"; 
        text += cars[5] + "<br>"; 
    }
```
-----
##### 5.js类型转换

`Number()`转换数值，`String()`转换字符串，`Boolean()`转换布尔值。

1. `javascript`中有五种可能包含数值的数据类型：
1 Number
2 String
3 Boolean
4 Object
5 Function
有三种**对象类型**：
1 Array
2 Date
3 Object
同时有两种不能包含值的数据类型：
1 null
2 undefined

2. `typeof`**运算符**确定变量数据类型，返回字符串
NaN 的数据类型是数值
数组的数据类型是对象
日期的数据类型是对象
null 的数据类型是对象
未定义变量的数据类型是 undefined
尚未赋值的变量的数据类型也是 undefined
无法使用 typeof 去判断 JavaScript 对象是否是数组（或日期）
```javascript
    typeof bill //"undefined"
    typeof NaN //"number"
    typeof [1,2] //"object"
    typeof new Date() // "object"
    typeof null //"object"
    typeof undefined //"undefined"
```
3. `constructor`属性返回所有 JavaScript 变量的构造器函数
```javascript
    "Bill".constructor                 // 返回 "function String()  { [native code] }"
    (3.14).constructor                 // 返回 "function Number()  { [native code] }"
    false.constructor                  // 返回 "function Boolean() { [native code] }"
    [1,2,3,4].constructor              // 返回 "function Array()   { [native code] }"
    {name:'Bill', age:62}.constructor  // 返回" function Object()  { [native code] }"
    new Date().constructor             // 返回 "function Date()    { [native code] }"
    function () {}.constructor         // 返回 "function Function(){ [native code] }"
```
###### 检查某个对象是否为数组
```javascript
    function isArray(myArray){
        return myArray.constructor.toString().indexOf(Array) > -1; //和-1做比较，返回true/false
        //indexOf()找不到字符则返回-1
    }
```
###### 检查对象是否为数组函数
```javascript
    function isArray(myArray){
        return myArray.constructor === Array; //Array.constructor
    }
```
4. `JavaScript `变量能够被转换为新变量以及另一种数据类型：
通过使用 `JavaScript `函数
通过 `JavaScript`本身自动转换
- 把数值转换为字符串
`String(1)`/`1.toString()`
- 把布尔转换为字符串
`String(true)`/`true.toString()`
- 把日期转换为字符串
`String(Date())`/`Date().toString()`/`getDate()`//获取字符串类型
- 把字符串转换为数值
`Number()`
`Number("99 88")   // 返回 NaN`将其他字符串转换为`NaN`
`parseInt()`
`parseFloat()`
- 一元 + 运算符
一元的 + 运算符可用于把变量转换为数字
`var y = "5";      // y 是字符串`
`var x = + y;      // x 是数字`
如果无法转换变量，则仍会成为数字，但是值为 NaN（Not a number）：
`var y = "Bill";   // y 是字符串`
`var x = + y;      // x 是数字 (NaN)`
- 把布尔转换数值
`Number(true)`
- 把日期转换为数子
全局方法
`d = new Date();`
`Number(d)          // 返回 1572549938324`
日期方法
`d = new Date();`
`d.getTime()        // 返回 1572549938324`
- 自动类型转换
如果 JavaScript 尝试操作一种“错误”的数据类型，它会试图将该值转换为“正确”的类型。
JavaScript 自动调用变量的 toString() 函数，当您试图“输出”对象或变量时。
---
##### 6.位运算符

- 负数是正数的二进制补码加 1
按位与`&`
按位或`|`
按位非`~`
按位异或`^`
零填充左位移`<<`
有符号右位移`>>`
零填充右位移`<<<`

###### 进制转换
**右移0位：5>>>0/5>>0**
相当于取整，将字符串转换为数字类型，有符号5>>0只能处理非负数
```javascript
    numround = function (num){
        return parseInt(Number(num)/0);
    }
```
- 把十进制转换为二进制
**右移0位：5>>>0/5>>0**
相当于取整，将字符串转换为数字类型，有符号5>>0只能处理非负数
```javascript
    numround = function (num){
        return parseInt(Number(num)/0);
    }
```
```javascript
    5.toString() //会被误认为5.xxxx
    // VM5840:1 Uncaught SyntaxError: Invalid or unexpected token
    5.0.toString() //"5"
    ////////
    //转换
    function dec2bin(dec){
        return (dec>>>0).toString(2);
    }
```
- 把二进制转换为十进制
```javascript
    function bin2dec(bin){
        return parseInt(bin,2).toString(10)
    }
```
- `parseInt`
1. 基本用法（只接受一个参数，可以当做第二个参数默认是10）：parseInt的返回值只有两种可能，不是一个十进制整数，就是NaN。
`parseInt()`返回数值
2. 进制转换（接收两个参数)
`parseInt(string, radix)`可接收两个参数，`parseInt(0101,2) //返回5`
---
##### 7.正则表达式
正则表达式是构成搜索模式的字符序列，可用于文本搜索和文本替换操作。
语法：`/pattern/modifiers;`

- 正则表达式中常用两个字符串方法`search()`和`replace()`
`search()` 方法使用表达式来搜索匹配，然后返回匹配的位置。
`replace()` 方法返回模式被替换处修改后的字符串。
```javascript
    //search()
    //字符串方法
    var str = "Visit W3School!";
    var n = str.search("W3School"); 
    //正则表达式
    var str = "Visit W3School";
    var n = str.search(/w3school/i);    
```
```javascript
    //replace()
    //字符串方法
    var str = "Visit Microsoft!";
    var res = str.replace("Microsoft", "W3School"); 
    //正则表达式
    var str = "Visit Microsoft!";
    var res = str.replace(/microsoft/i, "W3School");  
```
- 正则表达式修饰符
`i`	执行对大小写不敏感的匹配。
`g`	执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。
`m`	执行多行匹配。
- 正则表达式模式
1. 括号用于查找一定范围的字符串：
`[abc]`	查找方括号之间的任何字符。
`[0-9]`	查找任何从 0 至 9 的数字。
`(x|y)`	查找由 | 分隔的任何选项。
2. 元字符（Metacharacter）是拥有特殊含义的字符：
`\d`	查找数字。
`\s	`查找空白字符。
`\b`	匹配单词边界。
`\uxxxx`	查找以十六进制数 xxxx 规定的 Unicode 字符。
3. Quantifiers 定义量词：
`n+`	匹配任何包含至少一个 n 的字符串。
`n*`	匹配任何包含零个或多个 n 的字符串。	
`n?`	匹配任何包含零个或一个 n 的字符串。
- RegExp 对象
- `test()`
`test()` 是一个正则表达式方法。
它通过模式来搜索字符串，然后根据结果返回 `true `或 `false`。
```javascript
    var pattern = /e/;
    pattern.test("The best things in life are free!");//true
```
- `exec()`
`exec()` 方法是一个正则表达式方法。
它通过指定的模式（`pattern`）搜索字符串，并返回已找到的文本。
```javascript
    var pattern = /e/;
    var obj = pattern.exec("The best things in life are free!");
    obj
    //["e", index: 2, input: "The best things in life are free!", groups: undefined]
    obj[0]
    //"e"
    obj.index
    //2
    obj.input
    //"The best things in life are free!"
```
---
##### 8.异常
`try` 语句使您能够测试代码块中的错误。

`catch` 语句允许您处理错误。

`throw `语句允许您创建自定义错误。

`finally `使您能够执行代码，在 `try` 和 `catch `之后，无论结果如何。

###### try-catch语句
- 把所有可能抛出错误的代码放在`try{}`语块中，把用于错误处理的语句放在`catch{}`中
```javascript
    try{
        //可能会导致错误的代码
    } catch(error){
        //在错误发生时怎么处理
    }
```
如果`try{}`中任何代码发生了错误，就会立即退出代码执行过程，然后执行`catch{}`。

然后`catch{}`会接收到一个包含错误信息的对象，这个对象必须有名字，并且有包含错误信息的`message`属性，`name`属性保存错误类型。

所有浏览器都支持`message`属性，跨浏览器时最好只使用`message`属性。
```javascript
    try{
        window.somenonexistentFunction();
    } catch(error){
        alert(error.message);
    }
```
- `finally`总是会被执行
```javascript
    try{
        //可能会导致错误的代码
    } catch(error){
        //在错误发生时怎么处理
    } finally{
        无论 try / catch 结果如何都执行的代码块
    }
```
- 错误类型
1 `Error `基类型，其他错误类型都继承自该类型，错误对象中的方法全是默认的对象方法,基类型的主要目的是供开发人员抛出自定义错误。
2 `EvalError `在使用 `eval()`函数而发生异常时被抛出，即如果没有把 `eval()`当成函数调用，就会抛出错误。`eval()`可以计算`String`表达式
`new eval(); //抛出 EvalError`
`eval = foo;//抛出 EvalError `
3 `RangeError ` ：数值超出范围时触发
4 `ReferenceError ` ：找不到对象的情况下触发
5 `SyntaxError ` ：有语法错误的代码传入`eval()`时触发
6 `TypeError ` ：变量类型不符合要求
7 `URIError` ：`encodeURI()` `decodeURI()` `URI`格式不正确
```javascript
    try { 
        someFunction(); 
    } catch (error){ 
        if (error instanceof TypeError){ 
            //处理类型错误 
        } else if (error instanceof ReferenceError){ 
            //处理引用错误 
        } else { 
            //处理其他类型的错误 
        }
    }
```
- 抛出错误
当发生错误时，`JavaScript `通常会停止并产生错误消息，即`JavaScript `将抛出异常（抛出错误）。
`JavaScript` 实际上会创建带有两个属性的 `Error` 对象：`name` 和 `message`。

**throw**
抛随时出自定义错误，必须给定`throw`操作符一个指定的值，值的类型无要求。

在遇到`throw`操作符时，代码立即停止执行。当且仅当`try-catch`捕获到被抛出的值时，代码才会继续被执行。
```javascript
<!DOCTYPE html>
<html>
<body>

<p>请输入 5 到 10 之间的数字：</p>

<input id="demo" type="text">
<button type="button" onclick="myFunction()">检测输入</button>

<p id="p01"></p>

<script>
function myFunction() {
  var message, x;
  message = document.getElementById("p01");
  message.innerHTML = "";
  x = document.getElementById("demo").value; //input value
  try { 
    if(x == "")  throw "是空的";
    if(isNaN(x)) throw "不是数字";
    x = Number(x);
    if(x > 10)   throw "太大";
    if(x < 5)  throw "太小";
  }
  catch(err) {
    message.innerHTML = "输入：" + err;
  }
  finally {
    document.getElementById("demo").value = "";
  }
}
</script>

</body>
</html>
```
----
##### 9.作用域
1. 作用域是指有权访问的变量集合，`js`中有两种作用域：
    - 局部作用域
    - 全局作用域
`js`中函数会创建自己的作用域，函数内部定义的变量从函数外部是无法访问的。

2. 局部变量：在函数中使用`var`声明的变量，只能在函数内部访问，从函数外部是无法访问的。
   - 可以在不同函数中声明同名的局部变量。
  

3. 全局变量：函数之外声明的变量
   - 全局变量的作用域是全局的：网页的所有脚本和函数都能够访问它。
   - **自动全局：如果您为尚未声明的变量赋值，此变量会自动成为全局变量。**
   - 在“严格模式”中不会自动创建全局变量。
   - 在 HTML 中，全局作用域是 window。所有全局变量均属于 window 对象。

- 局部变量会在函数完成时被删除。
- 全局变量会在您关闭页面是被删除。
- 函数参数也是函数内的局部变量。
---
##### 10.提升Hoisting
- 在 JavaScript 中，可以在使用变量之后对其进行声明。即可以在声明变量之前使用它。
- `js`中`var a = 1;` => `var a; a = 1;`
- **函数提升在变量提升之上**
- Hoisting 是 JavaScript 将所有声明提升到**当前作用域**顶部的默认行为
- 用 `let `或 `const` 声明的变量和常量不会被提升
- 始终在每个作用域的开头声明所有变量!
- 严格模式中不允许使用未声明的变量
----
##### 11.严格模式
- `"use strict"; `定义 `JavaScript` 代码应该以“严格模式”执行。
- 在严格模式中，不能使用未声明的变量
- `"use strict"` 指令只能在脚本或函数的开头被识别
```javascript
    "use strict";
    myFunction();

    function myFunction() {
        y = 3.14;   // 这会引发错误，因为 y 尚未声明
    }
```
- 在函数中声明严格模式，拥有局部作用域（只有函数中的代码以严格模式执行）：
```javascript
    x = 3.14;       // 这不会引发错误
    myFunction();

    function  myFunction() {
        "use strict";
        y = 3.14;   // 这会引发错误
    }
```
- 在严格模式中，错误输入变量名不会创建新的全局变量，而是会抛出错误。向不存在的变量赋值也会抛出错误。
在严格模式中，向不可写的、只能读取的、不存在的属性赋值，或者向不存在的变量或对象赋值，将抛出错误。
具体情况参考 - [严格模式w3school](https://www.w3school.com.cn/js/js_strict.asp)

---
##### 12.this
1. 在方法中，`this`指的是方法的拥有者对象
```javascript
    var person = {
    firstName: "Bill",
    lastName : "Gates",
    id       : 678,
    fullName : function() {
        return this.firstName + " " + this.lastName;
    }
    };
```
2. 在函数中，`this`指的是全局对象，严格模式下`this`是`undefined`
在 `JavaScript` 函数中，函数的拥有者默认绑定 `this`。

3. 在（`DOM`）事件中，指的是接收此事件的元素
```javascript
    <button onclick="this.style.display='none'">
    点击来删除我！
    </button>
```
4. 单独使用，指的是全局对象
- 对象方法绑定
`var person = {
  firstName  : "Bill"}`
`this.firstName`
- 显式函数绑定 `call()`，`apply()`
```javascript
    var person1 = {
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
    }
    var person2 = {
    firstName:"Bill",
    lastName: "Gates",
    }
    person1.fullName.call(person2);  // 会返回 "Bill Gates"
```
##### 13.let & const
`let`和`const`为j`s`提供了块级作用域变量，在这之前`js`只有全局作用域和函数作用域。
- 全局（在函数之外）声明的变量拥有全局作用域。全局变量可以在 JavaScript 程序中的任何位置访问。
- 局部（函数内）声明的变量拥有函数作用域。局部变量只能在它们被声明的函数内访问。
###### let
**块级作用域**
- 通过`var`声明的变量没有块级作用域。
- 为什么要使用`let`和`const`？
    重新声明变量：
    使用 var 关键字重新声明变量会带来问题。
    在块中重新声明变量也将重新声明块外的变量：
```javascript
    var x = 10;
    // 此处 x 为 10
    { 
    var x = 6;
    // 此处 x 为 6
    }
    // 此处 x 为 6
```
而使用`let`没有这个问题,使用` let `关键字重新声明变量可以解决这个问题。
在块中重新声明变量不会重新声明块外的变量：
```javascript
    var x = 10;
    // 此处 x 为 10
    {
        let x = 6;
        // 此处 x 为 6
    }
    // 此处 x 为 10
```
- 循环作用域

`var`
```javascript
    var i = 7;
    for (var i = 0; i < 10; i++) {
    // 一些语句
    }
    // 此处，i 为 10
```
`let`
```javascript
    let i = 7;
    for (let i = 0; i < 10; i++) {
    // 一些语句
    }
    // 此处 i 为 7
```
- 在全局作用域和函数作用域中两者相似
- `HTML`中的全局变量
在`HTML`中全局作用域是window对象

通过 `var` 关键词定义的全局变量属于 `window `对象
```javascript
    var carName = "porsche";
    // 此处的代码可使用 window.carName
```
通过 `let `关键词定义的全局变量不属于 `window `对象
```javascript
    let carName = "porsche";
    // 此处的代码不可使用 window.carName
```
- 重新声明
    - 允许在程序的任何位置使用 `var` 重新声明 `JavaScript` 变量
    - 在相同的作用域，或在相同的块中，通过` let `重新声明一个 `var `变量是不允许的
    - 在相同的作用域，或在相同的块中，通过 `let `重新声明一个`let `变量是不允许的在相同的作用域，或在相同的块中，通过 `var `重新声明一个 `let `变量是不允许的
    - 在不同的作用域或块中，通过 let 重新声明变量是允许的
- 提升
   -  通过` var `声明的变量会提升到顶端，可以在声明变量之前就使用它。
   - 通过 `let `定义的变量不会被提升到顶端。在声明 `let `变量之前就使用它会导致` ReferenceError`。

###### const
- 在块作用域内使用 const 声明的变量与 let 变量相似。
- 通过 `const `定义的变量与 `let` 变量类似，但**不能重新赋值**：
```javascript
    const PI = 3.141592653589793;
    PI = 3.14;      // 会出错
    PI = PI + 10;   // 也会出错
```
- `JavaScript` `const `变量必须在**声明时赋值**：
```javascript
    //wrong
    //const PI;
    //PI = 3.14159265359;

    //correct
    const PI = 3.14159265359;
```
- 不可以改变常量值，但可以改变常量对象
```javascript
    // 您可以创建 const 对象：
    const car = {type:"porsche", model:"911", color:"Black"};

    // 您可以更改属性：
    car.color = "White";

    // 您可以添加属性：
    car.owner = "Bill";

    // ERROR
    const car = {type:"porsche", model:"911", color:"Black"};
    car = {type:"Volvo", model:"XC60", color:"White"};    // ERROR
```
- 重新声明
在不同的作用域或块中重新声明 `const `是允许的。
- 提升
通过 `const` 定义的变量不会被提升到顶端。`const `变量不能在声明之前使用。

-----
##### 14.样式指南
[代码规范](https://github.com/Chihihill/spec/blob/master/javascript-style-guide.md)
用字符串-字符串返回`NaN`
`==` 比较运算符总是在比较之前进行类型转换（以匹配类型）。

`===` 运算符会强制对值和类型进行比较。
`switch` `'10' != 10`

带有命名索引的数组被称为关联数组（或散列）。

`JavaScript `不支持带有命名索引的数组。

在` JavaScript `中，数组使用数字索引。

在 `JavaScript` 中，对象使用命名索引。

如果您使用命名索引，那么在访问数组时，`JavaScript` 会将数组重新定义为标准对象。

在自动重定义之后，数组方法或属性将产生未定义或非正确的结果
```javascript
    var person = [];
    person["firstName"] = "Bill";
    person["lastName"] = "Gates";
    person["age"] = 46;
    var x = person.length;         // person.length 将返回 0
    var y = person[0];              // person[0] 将返回 undefined
```
`null` is an object, but undefined is not an object
We can use `typeof myobj === 'undefined' `to identify the object exist or not.
But we cannot use `typeof myobj === 'null'`, becasue if the object is not identifyed, there would be sth wrong.

[判断对象是否存在](https://www.cnblogs.com/pekkle/p/7196024.html)

-------
##### 15.js性能

- 减少循环中的活动
```javascript
    var i = 0;
    var I = arr.length;
    for(i; i < I; i++){}
```
- 减少DOM访问
把DOM元素变成本地变量
```javascript
    var obj = document.getElementById("demo");
    obj.innerText = 'hello';
```
- 缩减DOM规模
减少页面中的DOM元素数量，所以，每次搜索DOM元素都能减少时间。
- 避免不必要的变量
避免不打算储值的变量
```javascript
    var fullName = firstName + " " + lastName;
    document.getElementById("demo").innerHTML = fullName; 

    //===>
    document.getElementById("demo").innerHTML = firstName + " " + lastName;
```
- 延迟 JavaScript 加载
请把脚本放在页面底部，使浏览器首先加载页面。
`HTTP `规范定义浏览器不应该并行下载超过两种要素。
在`script`标签中使用 `defer=“true”`
`defer `属性规定了脚本应该在页面完成解析后执行，但它只适用于外部脚本。
`window.onload = downScripts;`
- 避免使用 `with`

##### 16.ES5
`String.trim()` 删除字符串两端的空白字符。
```javascript
    var str = "       Hello World!        ";
    alert(str.trim());
```
- `JSON.parse()`
JavaScript 函数 JSON.parse() 用于将文本转换为 JavaScript 对象：
```javascript
    var obj = JSON.parse('{"name":"Bill", "age":62, "city":"Seatle"}');
```
- `JSON.stringify()`
- `Date.now()`
`Date.now() `返回自零日期（`1970 年 1 月 1 日 00:00:00:00`）以来的毫秒数。
- `Object.defineProperty()`
允许定义对象属性和/或更改属性的值和/或元数据。
```javascript
    // 创建对象：
    var person = {
    firstName: "Bill",
    lastName : "Gates",
    language : "NO", 
    };

    // 更改属性：
    Object.defineProperty(person, "language", {
    value: "EN",
    writable : true,
    enumerable : true,
    configurable : true
    });

    // 枚举属性
    var txt = "";
    for (var x in person) {
    txt += person[x] + "<br>";
    }
    document.getElementById("demo").innerHTML = txt;
```
```javascript
    // 创建对象：
    var person = {
    firstName: "Bill",
    lastName : "Gates",
    language : "NO"
    };

    // 更改属性：
    Object.defineProperty(person, "language", {
    get : function() { return language },
    set : function(value) { language = value.toUpperCase()}
    });

    // 更改语言
    person.language = "en";

    // 显示语言
    document.getElementById("demo").innerHTML = person.language;
```
- `charAt()`
-----
##### 17.ES6
-----
##### 18.JSON

`JSON` 是存储和传输数据的格式。
`JSON` 经常在数据从服务器发送到网页时使用。

`JSON` 指的是 `JavaScript Object Notation`
`JSON `是轻量级的数据交换格式
`JSON` 独立于语言` *`;* JSON 的语法是来自 JavaScript 对象符号的语法，但 JSON 格式是纯文本。读取和生成 JSON 数据的代码可以在任何编程语言编写的。
`JSON` 是“自描述的”且易于理解
```json
{
"employees":[
    {"firstName":"Bill", "lastName":"Gates"}, 
    {"firstName":"Steve", "lastName":"Jobs"},
    {"firstName":"Alan", "lastName":"Turing"}
]
}
```

`JSON` 格式评估为 `JavaScript` 对象
`JSON` 格式在语法上与创建 `JavaScript` 对象的代码相同。
由于这种相似性，`JavaScript` 程序可以很容易地将 `JSON `数据转换成本地的 `JavaScript` 对象。

**JSON 语法规则**
数据是名称/值对
数据由逗号分隔
花括号保存对象
方括号保存数组

**把 JSON 文本转换为 JavaScript 对象**
1. 创建包含JSON格式的javascript字符串
```javascript
var text = '{ "employees" : [' +
'{ "firstName":"Bill" , "lastName":"Gates" },' +
'{ "firstName":"Steve" , "lastName":"Jobs" },' +
'{ "firstName":"Alan" , "lastName":"Turing" } ]}';
```
2. 使用`javascript`内建函数，`JSON.prase()`，把字符串转换为javascript对象
```javascript
var obj = JSON.prase(text);
```
3. 使用新对象
```javascript
<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML =
obj.employees[1].firstName + " " + obj.employees[1].lastName;
</script> 
```
------
##### 19.JS表单
HTML 表单验证能够通过 JavaScript 来完成。

- 如果某个表单字段（fname）是空的，那么该函数会发出一条警告消息，并返回 false，以防止表单被提交出去：
```javascript
<form name="myForm" action="/action_page_post.php" onsubmit="return validateForm()" method="post">
姓名：<input type="text" name="fname">
<input type="submit" value="Submit">
</form>

function validateForm() {
    var x = document.forms["myForm"]["fname"].value;
    //document.forms[表单名][输入框名]
    if (x == "") {
        alert("必须填写姓名");
        return false;//防止表单被提交
    }
}
```
- 验证1-10之间的数字
```javascript
function(){
var x, text;
x = document.getElementById("name").value;
if(isNaN(x) || x < 1 || x > 10){
    text = "invalid input";
} else {
    text = "valid input";
}
}
```

- 如果表单字段（fname）是空的，required 属性防止表单被提交：
```javascript
<form action="/action_page_post.php" method="post">
   <input type="text" name="fname" required>//required
   <input type="submit" value="Submit">
</form>
```

**数据验证**
数据验证指的是确保干净、正确和有用的用户输入的过程。

典型的验证任务是：

用户是否已填写所有必需的字段？
用户是否已输入有效的日期？
用户是否在数字字段中输入了文本？
大多数情况下，数据验证的作用是确保正确的用户输入。

验证可以通过很多不同的方法来定义，并且可以使用很多不同的方法来开发。

服务器端验证是由 web 服务器执行的，在输入被送往服务器之后。

客户端验证是由 web 浏览器执行的，在输入被送往 web 服务器之前。

**HTML 约束验证**
HTML5 引入了一种新的 HTML 验证概念，名为约束验证（constraint validation）。

- HTML 约束验证基于：
约束验证 HTML 输入属性
约束验证 CSS 伪选择器
约束验证 DOM 属性和方法
`disabled`	规定 input 元素应该被禁用
`max`	规定 input 元素的最大值
`min`	规定 input 元素的最小值
`pattern`	规定 input 元素的值模式
`required`	规定输入字段需要某个元素
`type`	规定 input 元素的类型

- 约束验证 CSS 伪选择器
`:disabled`	选择设置了 "disabled" 属性的 input 元素。
`:invalid	`选择带有无效值的 input 元素。
`:optional`	选择未设置 "required" 属性的 input 元素。
`:required`	选择设置了 "required" 属性的 input 元素。
`:valid	`选择带有有效值的 input 元素。
----
##### 20.表单API
- 约束验证 DOM 方法
`checkValidity()`	返回 true，如果 input 元素包含有效数据
`setCustomValidity()`	设置 input 元素的 validationMessage 属性
```javascript
<input id="id1" type="number" min="100" max="300" required>
<button onclick="myFunction()">OK</button>

<p id="demo"></p>

<script>
 function myFunction() {
    var inpObj = document.getElementById("id1");
    if (inpObj.checkValidity() == false) {
        document.getElementById("demo").innerHTML = inpObj.validationMessage;
        //validationMessage会显示具体输入错误信息
    }
}
</script>
```
- 约束验证 DOM 属性
`validity	`包含与 input 元素的合法性相关的布尔属性。
`validationMessage`	包含当 validity 为 false 时浏览器显示的消息。
`willValidate`	指示是否验证 input 元素。

- 合法性属性
input 元素的 validity 属性包含了与数据合法性相关的一系列属性：
1`customError`	设置为 true，如果设置自定义的合法性消息。
2`patternMismatch`	设置为 true，如果元素值不匹配其 pattern 属性。
3`rangeOverflow`	设置为 true，如果元素值大约其 max 属性。
4`rangeUnderflow`	设置为 true，如果元素值小于其 min 属性。
5`stepMismatch`	当字段拥有 step 属性，且输入的 value 值不符合设定的间隔值时，该属性值为 true。
6`tooLong`	设置为 true，如果元素值超过了其 maxLength 属性。
7`typeMismatch`	当字段的 type 是 email 或者 url 但输入的值不是正确的类型时，属性值为 true。
8`valueMissing`	设置为 true，如果元素（包含 required）没有值。
9`valid`	设置为 true，如果元素值是有效的。

- **rangeOverflow**
```javascript
<input id="id1" type="number" max="100">
<button onclick="myFunction()">OK</button>

<p id="demo"></p>

<script>
function myFunction() {
    var txt = "";
    if (document.getElementById("id1").validity.rangeOverflow) {
        //rangeOverflow
        txt = "值太大";
    }
     document.getElementById("demo").innerHTML = txt;
}
</script> 
```
----
#### 21.对象Object
##### 定义
所有 `JavaScript` 值，除了原始值，都是对象。
- JS原始值
没有属性和方法
原始数据类型指的是拥有原始值的数据。
5重原始数据类型：`string`,`number`,`boolean`,`null`,`undefined`
- 对象是包含变量的变量
JavaScript 对象是命名值的集合。
```javascript
var person = {firstName:"Bill", lastName:"Gates", age:62, eyeColor:"blue"};
```
- 对象属性
JavaScript 对象中的命名值，被称为属性。
- 对象方法
方法是可以在对象上执行的动作。
对象属性可以是原始值、其他对象以及函数。
对象方法是包含函数定义的对象属性。

**创建 JavaScript 对象**
有不同的方法来创建对象：
定义和创建单个对象，使用对象文字。
定义和创建单个对象，通过关键词 new。
定义对象构造器，然后创建构造类型的对象。
在 ECMAScript 5 中，也可以通过函数 Object.create() 来创建对象。
1. 使用对象字面量
```javascript
var person = {firstName:"Bill", lastName:"Gates", age:62, eyeColor:"blue"};
///
var person = {
    firstName:"Bill",
    lastName:"Gates",
    age:62,
    eyeColor:"blue"
};
```
2. 使用 JavaScript 关键词 new
```javascript
var person = new Object();
person.firstName = "Bill";
person.lastName = "Gates";
person.age = 50;
person.eyeColor = "blue"; 
```
**JavaScript 对象是易变的**
对象是易变的：它们通过引用来寻址，而非值。

如果 person 是一个对象，下面的语句不会创建 person 的副本：

`var x = person; ` // 这不会创建 person 的副本。
对象 x 并非 person 的副本。它就是 person。x 和 person 是同一个对象。

对 x 的任何改变都将改变 person，因为 x 和 person 是相同的对象。
```javascript
var person = {firstName:"Bill", lastName:"Gates", age:62, eyeColor:"blue"}
 
var x = person;
x.age = 10;           // 这将同时改变 both x.age 和 person.age
```
**JavaScript 变量不是易变的。只有 JavaScript 对象如此。**

##### 属性
属性指的是与 JavaScript 对象相关的值。
JavaScript 对象是无序属性的集合。
属性通常可以被修改、添加和删除，但是某些属性是只读的。
- 访问 JavaScript 属性
`object.propertyName`
`object['propertyName']`
`objectName[expression]       // x = "age"; person[x]`
表达式必须计算为属性名:
`person.firstname + " is " + person.age + " years old.";`
`person["firstname"] + " is " + person["age"] + " years old.";`

**for in 循环**
JavaScript for...in 语句遍历对象的属性。
```javascript
var person = {fname:"Bill", lname:"Gates", age:62}; 

for (x in person) {
    txt += person[x];
}
```

**添加新属性**
`person.nationality = "English";`

**删除属性**
```javascript
var person = {firstName:"Bill", lastName:"Gates", age:62, eyeColor:"blue"};
delete person.age;   // 或 delete person["age"];
```
delete 关键词会同时删除属性的值和属性本身。
delete 关键词不会删除被继承的属性，但是如果您删除了某个原型属性，则将影响到所有从原型继承的对象。

##### 方法
包含函数定义的属性

**this**
在 JavaScript 中，被称为 this 的事物，指的是拥有该 JavaScript 代码的对象。
- 创建对象方法
`methodName : function() { 代码行 }`
```javascript
// 创建对象：
var person = {
    firstName: "Bill",
    lastName : "Gates",
    id       : 12345,
    //对象方法
    fullName : function() {
       return this.firstName + " " + this.lastName;
    }
};
```
- 访问对象方法
`objectName.methodName()`

- 使用内建方法
使用 String 对象的 toUpperCase() 方法，把文本转换为大写：
```javascript
var message = "Hello world!";
var x = message.toUpperCase();
```
- 添加新的方法
向对象添加方法是在构造器函数内部完成的：
```javascript
function person(firstName, lastName, age, eyeColor) {
    this.firstName = firstName;  
    this.lastName = lastName;
    this.age = age;
    this.eyeColor = eyeColor;
    this.changeName = function (name) {
        this.lastName = name;
    };
}
```
------
##### 22.函数
在js中，函数 是对象的方法。
##### call()
- `call()`可以用来调用所有者对象作为参数的方法。通过`call()`可以使用属于另一个对象的方法。
```javascript
var person = {
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
}
var person1 = {
    firstName:"Bill",
    lastName: "Gates",
}
var person2 = {
    firstName:"Steve",
    lastName: "Jobs",
}
//调用 person 的 fullName 方法，并用于 person1
person.fullName.call(person1);  // return "Bill Gates"
```
- 带参数的`call()`
```javascript
var person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}
var person1 = {
  firstName:"Bill",
  lastName: "Gates"
}
person.fullName.call(person1, "Seattle", "USA");
```

---
##### allpy()
通过 `apply()` 方法，能够编写用于不同对象的方法。
-  `call()` 和 `apply()` 之间的区别:
`call()` 方法分别接受参数。
`apply()` 方法接受数组形式的参数。

JS中数组没有`Math.max()`方法，所以可以用
`Math.max.apply(null,[1,2,3])`
`Math.max(...arrayName)`

---
##### 闭包
[闭包Closure](http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)
`JS`中变量属于全局或者局部作用域，闭包能够实现全局变量局部化。

拥有相同名称的全局变量和局部变量是不同的变量。修改一个，不会改变其他。
不通过关键词 var 创建的变量总是全局的，即使它们在函数中创建。

**变量的生命周期**
全局变量活得和您的应用程序（窗口、网页）一样久。
局部变量活得不长。它们在函数调用时创建，在函数完成后被删除。
**this的指向是由它所在函数调用的上下文决定的，而不是由它所在函数定义的上下文决定的。**

**闭包就是能够读取其他函数内部变量的函数。**
- 闭包的用途
1 可以读取函数内部的变量；
2 让这些变量的值始终保持在内存中； e.g.计数器

-----
#### HTML DOM

DOM 是一项 W3C (World Wide Web Consortium) 标准。

DOM 定义了访问文档的标准：
“W3C 文档对象模型（DOM）是中立于平台和语言的接口，它允许程序和脚本动态地访问、更新文档的内容、结构和样式。”

HTML DOM 是 HTML 的标准对象模型和编程接口。它定义了：
1 作为对象的 HTML 元素
2 所有 HTML 元素的属性
3 访问所有 HTML 元素的方法
4  所有 HTML 元素的事件
换言之：HTML DOM 是关于如何获取、更改、添加或删除 HTML 元素的标准。

在` DOM` 中，所有` HTML` 元素都被定义为对象。
编程界面是每个对象的属性和方法。
`HTML DOM` 方法是您能够（在 `HTML `元素上）执行的动作。
`HTML DOM `属性是您能够设置或改变的 `HTML` 元素的值。


`getElementById` 方法
`querySelectorAll()`

`onload` 和 `onunload` 事件
`onchange` 事件
`onchange` 事件经常与输入字段验证结合使用。

`onmousedown`, `onmouseup` 以及 `onclick `事件
`onmousedown`, `onmouseup` 以及 `onclick `事件构成了完整的鼠标点击事件。

首先当鼠标按钮被点击时，`onmousedown `事件被触发；然后当鼠标按钮被释放时，`onmouseup` 事件被触发；最后，当鼠标点击完成后，`onclick `事件被触发。

**事件冒泡还是事件捕获？**
在 HTML DOM 中有两种事件传播的方法：冒泡和捕获。
事件传播是一种定义当发生事件时元素次序的方法。假如 `<div> `元素内有一个 `<p>`，然后用户点击了这个 `<p> `元素，应该首先处理哪个元素`“click”`事件？

在冒泡中，最内侧元素的事件会首先被处理，然后是更外侧的：首先处理 `<p>` 元素的点击事件，然后是 `<div> `元素的点击事件。
在捕获中，最外侧元素的事件会首先被处理，然后是更内侧的：首先处理 `<div>` 元素的点击事件，然后是` <p> `元素的点击事件。

事件监听`addEventListener`能够让多个事件依次发生，否则一般情况下，如果给一个dom对象绑定同一个事件，只有最后一个会生效。

`document.body`/`document.documentElement`可以访问完整文档


**`nodeName` 属性**
`nodeName` 属性规定节点的名称。

`nodeName` 是只读的
元素节点的 `nodeName `等同于标签名
属性节点的 `nodeName` 是属性名称
文本节点的 `nodeName` 总是 #text
文档节点的 `nodeName `总是 #document

**DOM节点**
1. 创建新的HTML节点
```javascript
//创建p元素
var p = document.createElement("p");
//增加文本节点
var node = document.createTextNode("text");
//将文本节点添加到p元素
p.appendChild(node);

//将p元素添加到已有元素
existElement.append(p);
```
2. `insertBefore()`
```javascript
//在父元素existElement中的p1元素前添加pNew元素
existElement.insertBefore(pNew,p1);
```
3. 删除已有HTML元素
删除某个元素的时候，我们需要知道它的父元素。
```javascript
parent.removeChild(child);
```
    可以通过`parentNode`属性快速找到元素的父元素
```javascript
child.parentNode.removeChild(child);
```

4. 替换HTML元素
在`parent`元素中，使用新元素`pNEW`替换原来的`p1`元素
```javascript
parent.replaceChild(pNew, p1);
```
5. 使用`getElementByTagName()`返回HTML Collection集合对象，HTML Collection具有length属性，可以遍历元素，但它并不是数组。
```javascript
var x = document.getElementsByTagName("p");
y = x[1];
```

6. NodeList
访问 HTMLCollection 项目，可以通过它们的名称、id 或索引号。
访问 NodeList 项目，只能通过它们的索引号。
只有 NodeList 对象能包含属性节点和文本节点。
```javascript
//选取所有p节点
var myNodeList = document.querySelectorAll("p");
```