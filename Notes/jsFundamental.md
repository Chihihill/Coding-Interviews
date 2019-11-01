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
