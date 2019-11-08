[toc]
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