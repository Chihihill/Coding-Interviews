## Array
---




#### 判断是否为数组
1. `Array.isArray`
```javascript
    var a = 122;
    Array.isArray(a); //false
```
2. 创建自己的`iaArray`函数
```javascript
    function isArray(inputArray){
        return inputArray.constructor.toString().indexOf('Array') > -1
    }
```
- `inputArray.constructor`返回`inputArray`的构造函数`function Array(){[Native code]}`
- `toString()`将原本`function`类型转换为字符串类型
- `indexOf('Array')`查找返回字符串中是否有字符串`Array`，有则输入为数组
- `> -1`是因为，`indexOf()`在能够查找到字符串的时候返回索引，查找不到即不存在该字符串的时候返回`-1`，`-1 > -1 //false`

3. `inputArray instanceof Array`
```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits instanceof Array     
    // true
```
----
#### 数组方法
1. `toString()`将数组转换为数组值
```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.toString();  
    //"Banana,Orange,Apple,Mango"
```
2. `join()`方法可以将数组所有元素合成一个字符串，并且可以指定分隔符
```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"] 
    fruits.join("|");
    //"Banana|Orange|Apple|Mango"
```
3. `pop()`方法从数组中删除最后一个元素，并返回最后一个元素的值
```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.pop();
    //"Mango"
```
4. `push()`方法向数组中添加一个新的元素，并返回数组的长度
```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.push('Strawberry');
    //5
```
5. `shift()`方法会删除首个数组元素，并把所有其他元素“位移”到更低的索引，返回被“位移出”的字符串
```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];  
    fruits.shift();
    //"Banana"
```
6. `unshift()`方法（在开头）向数组添加新元素，并向后移动旧元素，返回新数组的长度
```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];  
    fruits.unshift('Strawberry');
    //
    5
```
7. 可以直接使用`array.length = newItem`向数组末尾添加新元素
8. 更改元素直接`array[0] = newItem`
9. 删除元素不能直接使用`delete`，会在数组中留下`undefined`的空洞
##### 拼接数组
10. `splice()`接收多个参数

```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.splice(2, 2, "Lemon", "Kiwi"); 
    fruits; // ["Banana", "Orange", "Lemon", "Kiwi"]
```
- 第一个参数第一个参数（2）定义了应添加新元素的位置（拼接）。

- 第二个参数（2）定义应删除多少元素。

- 其余参数（“Lemon”，“Kiwi”）定义要添加的新元素。
- 返回新数组
##### 合并数组
11. `concat()`方法合并现有数组创建一个新数组，不会更改现有数组，返回一个新数组
```javascript
    var myGirls = ["Cecilie", "Lone"];
    var myBoys = ["Emil", "Tobias", "Linus"];
    var myChildren = myGirls.concat(myBoys); 
    myChildren;//["Cecilie", "Lone", "Emil", "Tobias", "Linus"]
```
- 也可合并三个数组
`var myChildren = arr1.concat(arr2, arr3);`
- 也可以接收数值作为参数,创建新的数组
`var arr1 = ["Cecilie", "Lone"];`
`var myChildren = arr1.concat(["Emil", "Tobias", "Linus"]); `

##### 裁剪数组
12. `slice()`方法用数组的某个片段切出新数组，不会修改原数组，返回新数组
```javascript
    var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
    var citrus = fruits.slice(1); 
    citrus;//["Orange", "Lemon", "Apple", "Mango"]
```
- 可以接收一个参数，表示从a开始到数组末尾
- 可以接收两个参数，`slice(a,b)`,表示从a到b，不包括b

----
#### 数组排序
1. `Array.forEach()`方法为每个数组元素调用一次函数（回调函数），不会创建新数组，仅仅调用一次
该函数有 3 个参数：项目值、项目索引、数组本身
```javascript
    var numbers = [45, 4, 9, 16, 25];
    numbers.forEach(myFunction);

    function myFunction(value, index, array) {
    console.log( value += 1); 
    }
    // 46
    // 5
    // 10
    // 17
    // 26
```
2. `Array.map()`方法通过对每个数组元素执行函数来**创建新数组**,
不会对没有值的数组元素执行函数,
不会更改原始数组
该函数有 3 个参数：项目值、项目索引、数组本身
```javascript
    var numbers = [45, 4, 9, 16, 25];
    numbers.map(myFunction);

    function myFunction(value, index, array) {
    return value +=1; 
    }
    //[46, 5, 10, 17, 26]
```
3. `Array.filter()`方法创建一个包含通过测试的数组元素的新数组，**返回新数组**
该函数有 3 个参数：项目值、项目索引、数组本身
```javascript
    var numbers = [45, 4, 9, 16, 25];
    var over18 = numbers.filter(myFunction);

    function myFunction(value, index, array) {
    return value > 18;
    }
    over18; //[45, 25]
```
4. `array.reduce()`**???**
5. `array.reduceRight`**???**
6. `Array.every()`方法检查**所有**数组值是否通过测试，**返回boolean**
该函数有 3 个参数：项目值、项目索引、数组本身
```javascript
    var numbers = [45, 4, 9, 16, 25];
    var allOver18 = numbers.every(myFunction);

    function myFunction(value, index, array) {
    return value > 18;
    }
    allOver18; //false
```
7. `Array.some()`方法检查**某些**数组值是否通过了测试,**返回boolean**
该函数有 3 个参数：项目值、项目索引、数组本身
```javascript
    var numbers = [45, 4, 9, 16, 25];
    var someOver18 = numbers.some(myFunction);

    function myFunction(value, index, array) {
    return value > 18;
    }
    someOver18; //true
```
8. `Array.indexOf()`方法在数组中搜索元素值并返回其位置
`array.indexOf(item, start)`必须输入`itme`，`start`可选,表示搜索的起始位置
```javascript
    var fruits = ["Apple", "Orange", "Apple", "Mango"];
    var a = fruits.indexOf("Apple");
```
9. `Array.lastIndexOf()`从数组结尾开始搜索
`array.lastIndexOf(item, start)`必须输入`itme`，`start`可选,表示搜索的起始位置
```javascript
    var fruits = ["Apple", "Orange", "Apple", "Mango"];
    var a = fruits.lastIndexOf("Apple");
```
10. `Array.find()`方法返回通过测试函数的第一个数组元素的值
该函数有 3 个参数：项目值、项目索引、数组本身
11. `Array.findIndex()`方法返回通过测试函数的第一个数组元素的索引
该函数有 3 个参数：项目值、项目索引、数组本身