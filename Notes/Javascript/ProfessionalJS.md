> Professional JavaScript
[toc]

## DOM、BOM、Script标签
### 什么是DOM？
### 什么是BOM？
### HTML中`<script>`标签
- `<src>` 属性
在解释器对script元素内部的所有代码求值完毕以前，页面中的其余内容都不会被浏览器加载或显示；

- 为什么`<script>`不放在`<head>`标签里？
游览器在遇到`<body>`标签时，才开始呈现内容，即在所有代码下载完成前，页面会空白

- `<defer>`延迟脚本 **只对外部脚本有效**

- `<async>`异步脚本 **只对外部脚本有效**
- 使用外部js文件的优势？
- 文档模式`DOCTYPE`
- `<noscript>`元素
  


--------
  
## ECMAScript语法基础
- 区分大小写
- 严格模式
- 松散类型的变量
不建议修改变量所保存的值的类型
- 局部变量VS全局变量
`var`所定义的变量是局部变量
- 数据类型
  5种基本数据类型：`Undefined、Null、Boolean、String、Number`
  1种复杂数据类型：`Object`
  - `typeof`检查数据类型
  ```jacascript
  typeof null; //object
  ```
  - `null`可以用来检查变量是否是对象
  - `null == undefined`
  - `NaN != NaN`
  - 把非数值转换为数值类型`Number() / parseInt() / parseLooat()`
  - `toString() VS String()`
  - **`Object()`**
- 操作符
  - 位操作符
    - 按位非`~`
    - 按位与`&`
    - 按位或`|`
    - 按位异或`^`
    - 左移`<<`
    - 有符号右移`>>` （以符号位填充）
    - 无符号右移`>>>` （以0填充）
  - 布尔操作符
    - 逻辑非
    - 逻辑与
    - 逻辑或


