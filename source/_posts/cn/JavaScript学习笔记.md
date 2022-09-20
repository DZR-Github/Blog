---
title: JavaScript学习笔记
catalog: true
date: 2022-09-18 19:51:55
subtitle: " "
header-img: /img/scenery/wave_bg1.jpg
sticky: 0
tags: JavaScript
categories: Web
---

## JavaScript学习笔记

### JavaScript

- ECMAScript(核心)

- DOM(文档对象模型)

- BOM(浏览器对象模型)

  

### script标签

​    在不使用defer和async属性的情况下，所有“script”元素会依照它们在网页中出现的次序被解释

​	defer：使脚本延迟解析、执行（延迟执行脚本）

​	async：立即下载脚本，但不阻止其他页面动作（异步执行脚本）



### 变量

- **var（减少使用）**

  **特点**

  - 作用域：一个函数内部或者全局
  - 提升，把所有的变量声明拉到函数作用域顶部
  - 可反复多次声明同一变量



- **let声明（推荐使用)**

  **特点**

  - 作用域：块，由最近的一对花括号{ }界定
  - 不会被提升
  - 不可重复声明
  - for循环内常用let声明变量，迭代变量不会渗透到循环体外部

- **const声明（推荐使用）**

  **特点**

  - const 的行为与 let 基本相同
  - 唯一一个重要的区别是用它声明变量时必须同时初始化变量
  - 尝试修改 const 声明的变量会导致运行时错误



### 数据类型

 6种简单数据类型：Undefined 、 Null 、 Boolean 、 Number 、String 和 Symbol

1种复杂数据类型：Object

可用typeof操作符确定数据类型

**用法：**

```javascript
let message
console.log(typeof message);
```





### 操作符

- **位操作符**

  - 按位非    ~

    按位非的最终效果是对数值取反并减 1

    （如 5 —> -6 ;  -3 —> 2 )

  - 按位与    &

    按位与操作在两个位都是 1 时返回 1，在任何一位是 0 时返回 0

  - 按位或    |

    按位或操作在至少一位是 1 时返回 1，两位都是 0 时返回 0

  - 按位异或    ^

    按位异或只在一位上是 1 的时候返回 1（两位都是 1 或 0，则返回 0）。

  - 左移     <<

    按照指定的位数将数值的所有位向左移动

  - 有符号右移     >>

    按照指定的位数将数值的所有位向右移动，同时保留符号（正或负）

  - 无符号右移    >>>
    无符号右移会将数值的所有 32 位都向右移

- **指数操作符     ****

​		如：`3**2       // 9`

​			不仅如此，还有指数赋值操作符  **=

```
	let  squared = 3;
	squared **= 2;
	console.log(squared); // 9
```



- **相等操作符**

  - 等于”== “ 和不等于“！=”      （会进行强制类型转换）
  - 全等（===）和不全等（ ==）       （全等不会进行强制类型转换）

- **条件操作符**

  语法：variable = boolean_expression ? true_value : false_value;





### 语句

- **for语句**

  - for循环

  - for  in

    特点

    - for-in 语句是一种严格的迭代语句，用于枚举对象中的非符号键属性

    - ECMAScript 中对象的属性是无序的，因此 for-in 语句不能保证返回对象属性的顺序

    语法：for (property in expression) statement

    例子：

    ```javascript
    for (const propName in window) {
    	document.write(propName);
    }                 // 使用 for-in 循环显示了 BOM 对象 window 的所有属性
    
    ```

    

  - for  of

    特点

    - for-of 语句是一种严格的迭代语句，用于遍历可迭代对象的元素
    - for-of 循环会按照可迭代对象的 next() 方法产生值的顺序迭代元素
    - 如果尝试迭代的变量不支持迭代，则 for-of 语句会抛出错误

    语法：for (property of expression) statement

    例子：

    ```javascript
    for (const el of [2,4,6,8]) {
    	document.write(el);
    }       // 依次输出元素2,4,6,8
    ```

    

- **标签语句**

  **特点**

  - 标签语句用于给语句加标签
  - 标签语句的典型应用场景是嵌套循环

​		语法：label: statement

​		例子：

```javascript
	start: for (let i = 0; i < count; i++) {
		console.log(i);
	}       // start 是一个标签，可以在后面通过 break 或 continue 语句引用
```



- **break 和 continue 语句**

​	例1：

​	

```javascript
	let  num = 0 ;
	outermost:
	for (let i = 0; i < 10; i++) {
		for (let j = 0; j < 10; j++) {
			if (i == 5 && j == 5) {
				break outermost;
			}
			num++;
		}
	}
	console.log(num); // 55
```

在此例中，添加标签不仅让 break 退出（使用变量 j 的）内部循环，也会退出（使用变量 i 的）外部循环

例2：

```javascript
	let num = 0;
	outermost:
	for (let i = 0; i < 10; i++) {
		for (let j = 0; j < 10; j++) {

			if (i == 5 && j == 5) {
				continue outermost;
			}
			num++;
		}
	}
	console.log(num); // 95
```

在此例中， continue 语句会强制循环继续执行，但不是继续执行内部循环，而是继续执行外部循环。
当 i 和 j 都等于 5 时，会执行 continue ，跳到外部循环继续执行，从而导致内部循环少执行 5 次，结
果 num 等于 95。



### 原始值和引用值

#### 原始值

概念：最简单的数据

**特点**

不能有属性。

在通过变量把一个原始值赋值到另一个变量时，原始值会被复制到新变量的位置，这两个变量可以独立使用，互不干扰



#### 引用值

概念：由多个值构成的对象

**特点**

可随时添加、修改和删除其属性和方法。

在把引用值从一个变量赋给另一个变量时，存储在变量中的值也会被复制到新变量所在的位置。区别在于，这里复制的值实际上是一个指针，它指向堆内存中的对象。操作完成后，两个变量实际上指向同一个对象，因此一个对象上面的变化会在另一个对象上反映出来。



#### 传递参数

在按值传递参数时，只会被复制到另一个局部变量。

在按引用传递参数时，值在内存中的位置会被保存在另一个局部变量，这意味着对本地变量的修改会反映到函数外部。



### 基本引用类型

##### :one:Date

创建日期对象：

`let now = new Date();     //当前时间 `

`let someDate = new Date("May 23, 2019");     //某一天`

```
// 本地时间 2005 年 5 月 5 日下午 5 点 55 分 55 秒
let allFives = new Date(2005, 4, 5, 17, 55, 55);   //零起点月数（1月是0，2月是1，以此类推）
```

```
let date1 = new Date(2019, 0, 1); // 2019 年 1 月 1 日
let date2 = new Date(2019, 1, 1); // 2019 年 2 月 1 日
console.log(date1 < date2); // true
console.log(date1 > date2); // false
//确定日期先后的一个简单方式
```



##### :two:Number

创建Number对象：

`let numberObject = new Number(10);`

 Number 类型还提供了几个用于将数值格式化为字符串的方法。
 **toFixed()** 方法返回包含指定小数点位数的数值字符串。

 **toExponential()** 返回以科学记数法（也称为指数记数法）表示的数值字符串。

**toPrecision()** 方法会根据情况返回最合理的输出结果，可能是固定长度，也可能是科学记数法形式。

 **Number.isInteger()** 方法，用于辨别一个数值是否保存为整数



##### :three:String

**创建String对象：**

`let stringObject = new String("hello world");`

**字符串操作方法：**

 **concat()** 用于将一个或多个字符串拼接成一个新字符串。（but,对于拼接多个字符串来说，使用加号更方便。）

从字符串中提取子字符串的方法： **slice() 、 substr() 、 substring()**

**字符串模式匹配方法：**

**match()**

语法：

```
stringObject.match(searchvalue)    //searchvalue：要检索的字符串值。
stringObject.match(regexp)         //regexp: 正则表达式或RegExp 对象。
```

返回值：存放匹配结果的数组。该数组的内容依赖于 regexp 是否具有全局标志 g。

**search()**

语法：

`stringObject.search(regexp)`

返回值：stringObject中第一个与regexp相匹配的字串的起始位置。

**字符串替换操作方法：**

**Replace()**

语法：

```
stringObject.replace(regexp/substr,replacement)
//   regexp/substr: 要替换的字串或者正则表达式（可添加g来选择全局替换）    replacement:替换文本
```

##### :five:Math

**min():** 获取最小值。

**max()**：获取最大值。

**ceil()：**向上舍入为最接近的整数。

**floor()：**向下舍入为最接近的整数。

**round()：**四舍五入。

**fround()：**返回最接近的单精度浮点值表示。

**random()：**返回一个0~1范围内的随机数。



### 集合引用类型

#### :one:object

创建object实例：

方式1：

```
let person = new Object();
person.name = "Nicholas";
person.age = 29;
```

方式2：

```
let person = {
name: "Nicholas",
age: 29
};
```

属性名可以是字符串或数值。

存取属性：

person['name'] ：适用于属性名中含有可能会导致语法错误，例如含有关键字、保留字、空格，或者属性名为变量。

person.name：常用，除了上述情况均可使用此方式。

#### :two:Array

数组中的每个槽位可以存储任意类型的数据，数组的大小是动态的，会随数据添加而自动增长。

**数组创建方式：**

`let colors = new Array();`

`let colors = new Array(20);   //初始化一个length为20的数组`

`let colors = ["red", "blue", "green"]; // 创建一个包含 3 个元素的数组`
`let names = []; // 创建一个空数组`
`let values = [1,2,]; // 创建一个包含 2 个元素的数组`

**检测数组：** Array.isArray() 方法（尽量别用instanceof，确保万无一失）

**迭代器方法：**

Array原型中的3个用于检测数组内容的方法：keys()、values()、entries()

**keys():** 返回数组索引 

**values():** 返回数组元素

**entries():** 返回索引/值对

```
const a = ["foo", "bar", "baz", "qux"];
const aKeys = Array.from(a.keys());
const aValues = Array.from(a.values());
const aEntries = Array.from(a.entries());
console.log(aKeys); // [0, 1, 2, 3]
console.log(aValues); // ["foo", "bar", "baz", "qux"]
console.log(aEntries); // [[0, "foo"], [1, "bar"], [2, "baz"], [3, "qux"]]
```

**栈方法:       push()、pop()**

栈：后进先出

**队列方法：   shift()、push()**

队列：先进先出

**排序方法：  reverse()、sort()**

sort():默认情况下按升序排列，可以接收一个比较函数，用于判断哪个值应该排在前面

```
var points = [40,100,1,5,25,10];
points.sort(function(a,b){return a-b});
console.log(points);      // 1，5，10，25，40，100
```

**操作方法**

- 强制打平数组

```
let colors = ["red", "green", "blue"];
let newColors = ["black", "brown"];
let moreNewColors = {
[Symbol.isConcatSpreadable]: true,   //设置此项强制打平数组
length: 2,
0: "pink",
1: "cyan"
};
newColors[Symbol.isConcatSpreadable] = false;
// 强制不打平数组
let colors2 = colors.concat("yellow", newColors);
// 强制打平类数组对象
let colors3 = colors.concat(moreNewColors);
console.log(colors); // ["red", "green", "blue"]
console.log(colors2); // ["red", "green", "blue", "yellow", ["black", "brown"]]
console.log(colors3); // ["red", "green", "blue", "pink", "cyan"]
```



- slice()： 用于创建一个包含原有数组中一个或多个元素的新数组
- splice()
  - 删除：需要给 splice() 传 2 个参数：要删除的第一个元素的位置和要删除的元素数量。可以从数组中删除任意多个元素，比如 splice(0, 2) 会删除前两个元素。
  - 插入：需要给 splice() 传 3 个参数：开始位置、0（要删除的元素数量）和要插入的元素，可以在数组中指定的位置插入元素。第三个参数之后还可以传第四个、第五个参数，乃至任意多个要插入的元素。比如， splice(2, 0, "red", "green") 会从数组位置 2 开始插入字符串"red" 和 "green" 。
  - 替换：splice() 在删除元素的同时可以在指定位置插入新元素，同样要传入 3 个参数：开始位置、要删除元素的数量和要插入的任意多个元素。要插入的元素数量不一定跟删除的元素数量一致。比如， splice(2, 1, "red", "green") 会在位置 2 删除一个元素，然后从该位置开始向数组中插入 "red" 和 "green" 
- 搜索和位置方法
  - indexOf()：可返回某个指定的字符串值在字符串中首次出现的位置。
  - lastIndexOf：可返回一个指定的字符串值最后出现的位置。
  - includes()： 返回布尔值，表示是否至少找到一个与指定元素匹配的项。
- 迭代方法
  - every() ：对数组每一项都运行传入的函数，如果对每一项函数都返回 true ，则这个方法返回 true 
  - filter() ：对数组每一项都运行传入的函数，函数返回 true 的项会组成数组之后返回。
  - forEach() ：对数组每一项都运行传入的函数，没有返回值。
  - map() ：对数组每一项都运行传入的函数，返回由每次函数调用的结果构成的数组。
  - some() ：对数组每一项都运行传入的函数，如果有一项函数返回 true ，则这个方法返回 true 。



**其他：**join()、toLocaleString() 、toString() 、valueOf()

#### :three:Map

与Object类似，但存在一些差异

**创建Map：**

`const m = new Map();`

```
// 使用嵌套数组初始化映射
const m1 = new Map([
["key1", "val1"],
["key2", "val2"],
["key3", "val3"]
]);
alert(m1.size); // 3
```

初始化之后，可以使用 set() 方法再添加键/值对。另外，可以使用 get() 和 has() 进行查询，可以通过 size 属性获取映射中的键/值对的数量，还可以使用 delete() 和 clear() 删除值。

`m.set("firstName", "Matt")；`

`m.delete("firstName"); // 只删除这一个键/值对`

`m.clear(); // 清除这个映射实例中的所有键/值对`

set() 方法返回映射实例，因此可以把多个操作连缀起来，包括初始化声明：
`const m = new Map().set("key1", "val1");`

#### 与Object的一些区别：

-  Object 只能使用数值、字符串或符号作为键， Map 可以使用任何 JavaScript 数据类型作为键。
-  Map 实例会维护键值对的插入顺序，因此可以根据插入顺序执行迭代操作。

**选择Map还是Object?**

1. 内存占用：给定固定大小的内存， Map 大约可以比 Object 多存储 50%的键/值对。
2. 插入性能：如果代码涉及大量插入操作，那么显然 Map 的性能更佳。
3. 查找速度：如果代码涉及大量查找操作，那么某些情况下可能选择 Object 更好一些。
4. 删除性能：Map 的 delete() 操作都比插入和查找更快。如果代码涉及大量删除操作，那么毫无疑问应该选择 Map 。

#### :four:Set

Set像是加强版的Map，值不可重复，有序，只有值无键（键与值相同）

创建Set：

`const m = new Set();`

```
// 使用数组初始化集合
const s1 = new Set(["val1", "val2", "val3"]);
alert(s1.size); // 3
```

初始化之后，可以使用 **add()** 增加值，使用 **has()** 查询，通过 **size** 取得元素数量，以及使用 **delete()**和 **clear()** 删除元素

```
const s = new Set();
alert(s.has("Matt")); // false
alert(s.size); // 0
s.add("Matt")
.add("Frisbie");
alert(s.has("Matt")); // true
alert(s.size); // 2
s.delete("Matt");
alert(s.has("Matt")); // false
alert(s.has("Frisbie")); // true
alert(s.size); // 1
s.clear(); // 销毁集合实例中的所有值
alert(s.has("Matt")); // false
alert(s.has("Frisbie")); // false
alert(s.size); // 0
```

**迭代器：**

可以通过**value()**方法及其别名方法**keys()**取得迭代器

可以把集合转换为数组：

```
const s = new Set(["val1", "val2", "val3"]);
console.log([...s]); // ["val1", "val2", "val3"];     //方式1
console.log(Array.from(s));                           //方式2
```

求交集、并集、差集：

```
  let set1=new Set([1,2,3]);
  let set2=new Set([4,3,2]);
  //并集
  let union=new Set([...set1,...set2]);
  console.log('union')
  console.log(union);      // 1,2,3,4
  //交集
  let intersect=new Set([...set1].filter(x=>set2.has(x)));
  console.log('intersect')
  console.log(intersect);   // 2,3
  //差集
  let diff=new Set([...set1].filter(x=>!set2.has(x)));
  console.log('diff')
  console.log(diff);         // 1
```

遍历

```
// for of
for(let item of set1){
  	console.log(item);
  }
//  forEach
set2.forEach(value=>{
    console.log(value);
  })
//  values()
for(let value of set1.values()){
   console.log(value);
  }
```

add的value为对象时，set不能去重

```
  let set1=new Set();
  set1.add({name:'Mike'});
  set1.add({name:'Mike'});
  console.log(set1);  //  Set(2),两个相同的值
```



### 对象

对象属性：数据属性、访问器属性



数据属性的4个特性：

Configurable:表示属性是否可以通过delete删除重新定义，是否可以修改它的特性，以及是否可以把它改为访问器属性。（默认情况下为true）

Enumerable:表示属性是否可以通过for-in循环返回。（默认情况下为true）

Writable:表示属性的值是否可以被修改。（默认情况下为true）

Value:包含属性实际的值。读取和写入属性值的位置

要修改属性的默认属性，须使用Object.defineProperty( )方法。



访问器属性：

访问器属性不包含任何值，不能直接定义，必须使用Object.defineProperty()。





通过Object.defineProperty( )、Object.defineProperties( )方法定义的属性的Configurable、Enumerable、Writable默认值为false。



**合并对象**

调用Object.assign()方法

```
let dest, src, result;
//简单复制
dest = {};
src = { id: 'src' };
result = Object.assign(dest, src);
// Object.assign 修改目标对象也会返回修改后的目标对象
console.log(dest === result); // true
console.log(dest !== src); // true
console.log(result); // { id: src }
console.log(dest); // { id: src }
```

```
//多个源对象
dest = {};
result = Object.assign(dest, { a: 'foo' }, { b: 'bar' });
console.log(result); // { a: foo, b: bar }
```

Object.assign()实际上对每个源对象执行的是浅复制。如果多个源对象都有相同的属性，则使用最后一个复制的值。不能在两个对象间转移获取函数和设置函数（:question:）。如果赋值期间出错，则操作会中止并退出，只完成部分复制。



**增强的对象语法**

1. 属性值的简写

属性名和变量名相同时：

```
let name = 'Matt';
let person = {
name: name
};
```

等价于

```
let name = 'Matt';
let person = {
name
};
```

2.可计算属性

动态属性赋值（使用中括号包围的对象属性键）

```
const nameKey = 'name';
const ageKey = 'age';
const jobKey = 'job';
let person = {
[nameKey]: 'Matt',
[ageKey]: 27,
[jobKey]: 'Software engineer'
};
console.log(person); // { name: 'Matt', age: 27, job: 'Software engineer' }
```

3.简写方法名

```
let person = {
sayName: function(name) {
console.log(`My name is ${name}`);
}
};
```

等价于

```
let person = {
sayName(name) {
console.log(`My name is ${name}`);
}
};
```



**对象解构**

```
let person = {
name: 'Matt',
age: 27
};
let { name: personName, age: personAge } = person;
console.log(personName); // Matt
console.log(personAge); // 27
```

若让变量直接使用属性的名称，可以简写

```
let person = {
name: 'Matt',
age: 27
};
let { name, age } = person;
console.log(name); // Matt
console.log(age); // 27
```





**工厂模式**

抽象创建特定对象的过程：

```
function createPerson(name, age, job) {
let o = new Object();
o.name = name;
o.age = age;
o.job = job;
o.sayName = function() {
console.log(this.name);
};
return o;
}
let person1 = createPerson("Nicholas", 29, "Software Engineer");
let person2 = createPerson("Greg", 27, "Doctor");
```



**构造函数模式**

构造函数首字母大写，非构造函数小写字母开头

创建构造函数实例，应用new操作符

```
function Person(name, age, job){
this.name = name;
this.age = age;
this.job = job;
this.sayName = function() {
console.log(this.name);
};
}
let person1 = new Person("Nicholas", 29, "Software Engineer");
let person2 = new Person("Greg", 27, "Doctor");
```

与工厂模式的区别：

- 没有显式地创建对象
- 属性和方法直接赋值给了this
- 没有return



**原型模式**

假定Person为一个构造函数

Person构造函数、Person的原型对象和Person的两个实例之间的关系：

Person.prototype指向原型对象，Person.prototype.contructor指回Person构造函数，Person的实例person1有一个内部属性指回Person.prototype,且person1与构造函数没有直接联系。实例person1可以调用原型对象Person.prototype的方法。



可以通过Object.create()来创建一个新对象，同时为其指定原型。

如果在实例中添加了一个与原型对象中同名的属性，那就会在实例中创建这个属性，这个属性会遮住原型对象上的属性。



使用delete操作符可以删除实例中的属性，使用hasOwnProperty()方法可以确定属性是位于实例上还是原型对象上，使用in操作符会在可以通过对象访问到指定属性时返回true（无论该属性在实例上还是原型对象上）



### 类

##### 类定义

定义类有两种主要方式：类声明和类表达式。

```
// 类声明
class Person {}
// 类表达式
const Animal = class {};
```

与函数表达式类似，类表达式在它们被求值前也不能引用。不过，与函数定义不同的是，虽然函数
声明可以提升，但类定义不能：

```
console.log(FunctionExpression); // undefined
var FunctionExpression = function() {};
console.log(FunctionExpression); // function() {}

console.log(FunctionDeclaration); // FunctionDeclaration() {}
function FunctionDeclaration() {}
console.log(FunctionDeclaration); // FunctionDeclaration() {}

console.log(ClassExpression); // undefined
var ClassExpression = class {};
console.log(ClassExpression); // class {}

console.log(ClassDeclaration); // ReferenceError: ClassDeclaration is not defined
class ClassDeclaration {}
console.log(ClassDeclaration); // class ClassDeclaration {}
```

另一个跟函数声明不同的地方是，函数受函数作用域限制，而类受块作用域限制















### 编程思想

- 命令式编程

​		命令式编程就是对硬件操作的抽象， 程序员需要通过指令，精确的告诉计算机干什么事情。

- **函数式编程**

​		着眼点是函数，而不是过程，它强调的是如何通过函数的组合变换去解决问题，而不是通过思考要写怎样的语句去解决问题。

​	**核心概念**

​		数据不可变： 它要求你所有的数据都是不可变的，这意味着如果你想修改一个对象，那你应该创建一个新的对象用来修改，而不是修改已有的对象。

​		无状态： 主要是强调对于一个函数，不管你何时运行，它都应该像第一次运行一样，给定相同的输入，给出相同的输出，完全不依赖外部状态的变化。



### 重排/重绘

#### 重排(Reflow)

**概念：**当DOM的变化影响了元素的几何信息(元素的的位置和尺寸大小)，浏览器需要重新计算元素的几何属性，将其安放在界面中的正确位置，这个过程叫做重排。重排也叫回流，简单的说就是重新生成布局，重新排列元素。

**触发重排的情况**

*   页面初始渲染，这是开销最大的一次重排
*   添加/删除可见的DOM元素
*   改变元素位置
*   改变元素尺寸，比如边距、填充、边框、宽度和高度等
*   改变元素内容，比如文字数量，图片大小等
*   改变元素字体大小
*   改变浏览器窗口尺寸，比如resize事件发生时
*   激活CSS伪类（例如：`:hover`）
*   设置 style 属性的值，因为通过设置style属性改变结点样式的话，每一次设置都会触发一次reflow
*   ==查询某些属性或调用某些计算方法==：offsetWidth、offsetHeight等，除此之外，当我们调用 `getComputedStyle`方法，或者IE里的 `currentStyle` 时，也会触发重排，原理是一样的，都为求一个“即时性”和“准确性”。

| 常见引起重排属性和方法  |           \--            |                \-- |        \-- |
| ----------------------- | :----------------------: | -----------------: | ---------: |
| width                   |          height          |             margin |    padding |
| display                 |       border-width       |             border |   position |
| overflow                |        font-size         |     vertical-align | min-height |
| clientWidth             |       clientHeight       |          clientTop | clientLeft |
| offsetWidth             |       offsetHeight       |          offsetTop | offsetLeft |
| scrollWidth             |       scrollHeight       |          scrollTop | scrollLeft |
| scrollIntoView()        |        scrollTo()        | getComputedStyle() |            |
| getBoundingClientRect() | scrollIntoViewIfNeeded() |                    |            |

**优化建议**：

重排的代价是高昂的，会破坏用户体验，并且让UI展示非常迟缓。通过减少重排的负面影响来提高用户体验的最简单方式就是尽可能的减少重排次数，重排范围。下面是一些行之有效的建议，大家可以用来参考。

**减少重排范围**

我们应该尽量以局部布局的形式组织html结构，尽可能小的影响重排的范围。

*   不要使用 table 布局，可能很小的一个小改动会造成整个 table 的重新布局。那么在不得已使用table的场合，可以设置table-layout:auto;或者是table-layout:fixed这样可以让table一行一行的渲染，这种做法也是为了限制reflow的影响范围。

**减少重排次数**

**:one:==样式集中改变==**

不要频繁的操作样式，对于一个静态页面来说，明智且可维护的做法是更改类名而不是修改样式，对于动态改变的样式来说，相较每次微小修改都直接触及元素，更好的办法是统一在 `cssText` 变量中编辑。虽然现在大部分现代浏览器都会有 `Flush` 队列进行渲染队列优化，但是有些老版本的浏览器比如IE6的效率依然低下。

==使用cssText时，要加上原来的样式的值，因为原来的cssText值会被销毁==

```
// bad
var left = 10;
var top = 10;
el.style.left = left + "px";
el.style.top = top + "px";

// 当top和left的值是动态计算而成时...
// better 
el.style.cssText += "; left: " + left + "px; top: " + top + "px;";    

// better
el.className += " className";


```

:two:**分离读写操作**

DOM 的多个读操作（或多个写操作），应该放在一起。不要两个读操作之间，加入一个写操作。

```
// bad 强制刷新 触发四次重排+重绘
div.style.left = div.offsetLeft + 1 + 'px';
div.style.top = div.offsetTop + 1 + 'px';
div.style.right = div.offsetRight + 1 + 'px';
div.style.bottom = div.offsetBottom + 1 + 'px';

// good 缓存布局信息 相当于读写分离 触发一次重排+重绘
var curLeft = div.offsetLeft;
var curTop = div.offsetTop;
var curRight = div.offsetRight;
var curBottom = div.offsetBottom;

div.style.left = curLeft + 1 + 'px';
div.style.top = curTop + 1 + 'px';
div.style.right = curRight + 1 + 'px';
div.style.bottom = curBottom + 1 + 'px';

```

原来的操作会导致四次重排，读写分离之后实际上只触发了一次重排，这都得益于浏览器的渲染队列机制：

> 当我们修改了元素的几何属性，导致浏览器触发重排或重绘时。它会把该操作放进渲染队列，等到队列中的操作到了一定的数量或者到了一定的时间间隔时，浏览器就会批量执行这些操作。

:three:**将 DOM 离线**

“离线”意味着不在当前的 DOM 树中做修改，我们可以这样做：

* 使用 display:none

  一旦我们给元素设置 `display:none` 时（只有一次重排重绘），元素便不会再存在在渲染树中，相当于将其从页面上“拿掉”，我们之后的操作将不会触发重排和重绘，添加足够多的变更后，通过 `display`属性显示（另一次重排重绘）。通过这种方式即使大量变更也只触发两次重排。另外，`visibility : hidden` 的元素只对重绘有影响，不影响重排。

* 通过 [documentFragment](https://link.juejin.cn/?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FDocumentFragment "https://developer.mozilla.org/zh-CN/docs/Web/API/DocumentFragment") 创建一个 `dom` 碎片,在它上面批量操作 `dom`，操作完成之后，再添加到文档中，这样只会触发一次重排。

* 复制节点，在副本上工作，然后替换它！（可以利用cloneNode()方法）



:four:**使用 absolute 或 fixed 脱离文档流**

使用绝对定位会使的该元素单独成为渲染树中 `body` 的一个子元素，重排开销比较小，不会对其它节点造成太多影响。当你在这些节点上放置这个元素时，一些其它在这个区域内的节点可能需要重绘，但是不需要重排。

:five:**优化动画**

* 可以把动画效果应用到 `position`属性为 `absolute` 或 `fixed` 的元素上，这样对其他元素影响较小。

  动画效果还应牺牲一些平滑，来换取速度，这中间的度自己衡量： 比如实现一个动画，以1个像素为单位移动这样最平滑，但是Layout就会过于频繁，大量消耗CPU资源，如果以3个像素为单位移动则会好很多

* 启用GPU加速 `GPU` 硬件加速是指应用 `GPU` 的图形性能对浏览器中的一些图形操作交给 `GPU` 来完成，因为 `GPU` 是专门为处理图形而设计，所以它在速度和能耗上更有效率。

  `GPU` 加速通常包括以下几个部分：Canvas2D，布局合成, CSS3转换（transitions），CSS3 3D变换（transforms），WebGL和视频(video)。

  ```
    /*
    * 根据上面的结论
    * 将 2d transform 换成 3d
    * 就可以强制开启 GPU 加速
    * 提高动画性能
    */
    div {
      transform: translate3d(10px, 10px, 0);
    }
  
  ```



#### 重绘(Repaint)

**概念：**当一个元素的外观发生改变，但没有改变布局,重新把元素外观绘制出来的过程，叫做重绘。

**常见的引起重绘的属性：**

| 属性：          |       \--        |                 \-- |               \-- |
| --------------- | :--------------: | ------------------: | ----------------: |
| color           |   border-style   |          visibility |        background |
| text-decoration | background-image | background-position | background-repeat |
| outline-color   |     outline      |       outline-style |     border-radius |
| outline-width   |    box-shadow    |     background-size |                   |





### 文档碎片

概念：可以理解为是一个容器，可以临时存放DOM元素。

适用场景：为DOM树新增多个节点时。

若直接将这些节点插入DOM中则会触发多次重排，降低性能，使用文档碎片可以一次性添加多个节点而只触发一次重排，从而达到提升性能的目的（理论上）。

语法：

:one:`let fragment = document.createDocumentFragment();`

:two:`let fragment = new DocumentFragment();`

代码示例：

```
<body>
    <div id="t1">t1</div>
    <button onclick="insert()">insert</button>
    <script>
        function insert() {
            let frag = document.createDocumentFragment()   //新建一个文档碎片
            let p = document.createElement('p')
            p.innerHTML = 'p'
            let div = document.createElement('div')
            div.innerHTML = 'div'
            frag.appendChild(p)                       //在文档碎片中添加元素
            frag.appendChild(div)
            document.querySelector('#t1').appendChild(frag)   //将文档碎片中的元素插入DOM中
        }
    </script>
</body>

```





## 区分

:one:对象

- 对象的键，又称对象的属性

  设置方式：

  ```javascript
  var data = {
  	key1: '方式1'
  };
  data['key2'] = "方式2";
  var variable = 'key3';
  data[variable] = "方式3";
  data.key4 = "方式4";
  console.log(data);  //{key1: "方式1",key2: "方式2",key3: "方式3"，key4: "方式4"}
  ```

  

:two:原型对象(所有的 JavaScript 对象都会从一个 prototype（原型对象）中继承属性和方法)

对象的构造器(一个已存在构造器的对象中是不能添加新的属性)

```javascript
function Person(first, last, age, eyecolor) {
 this.firstName = first;
 this.lastName = last;
 this.age = age;
 this.eyeColor = eyecolor;
 }
 var myFather = new Person("John", "Doe", 50, "blue");
 var myMother = new Person("Sally", "Rally", 48, "green");
```

`Person.nationality = "English";`     :x:     (错误做法)

使用 prototype 属性就可以给对象的构造函数添加新的属性

`Person.prototype.nationality = "English";`      :white_check_mark:        (正确做法)



:one:children

children 属性返回元素的子元素的集合，是一个 HTMLCollection 对象。



:two:childNodes

childNodes 属性返回包含被选节点的子节点的 NodeList。







### 一些Question

#### Q1：undefined与null的区别？

- undefined代表定义未赋值
- null定义并赋值了，只是值为null

#### Q2：什么时候需要赋值为null？

- 初始赋值，表明将要赋值为对象
- 结束前，让对象变为垃圾对象（被垃圾回收器回收）

#### Q3：什么是数据？

存储在内存中代表特定信息的东西，本质上是010101……

**特点：**可传递、可运算

#### Q4：严格区别变量类型和数据类型？

**变量的类型（变量内存值的类型）：**

- 基本类型：保存的就是基本类型的数据
- 引用类型：保存的是地址值

**数据类型：**

- 基本类型
- 对象类型

#### Q5：什么是内存？

内存条通电后产生的可储存数据的空间（临时的）

**内存分类：**

- 栈：全局变量/局部变量
- 堆：对象

#### Q6：什么是变量？

- 可变化的量，由变量名和变量值组成
- 每个变量都对应一小块内存，变量名用来查找对应的内存，变量值就是内存中保存的数据

#### Q7：js调用函数时传递变量参数，是值传递还是引用传递？

* 理解1：都是值传递

* 理解2：可能是值传递，也可能是引用传递（地址值）

#### Q8：内存，数据，变量三者之间的关系？

- 内存是用来储存数据的空间
- 变量是内存的标识

#### Q9：对象？

- 多个数据的封装体
- 用来保存多个数据的容器（统一管理多个数据）
- 一个对象代表现实中的一个事物

#### Q10：对象的组成？

- 属性：属性名（字符串）和属性值（任意）组成
- 方法：一种特别的属性（属性值是函数）









