# 变量

**alert(msg)**	浏览器弹出警示框

**console.log(msg)**	浏览器控制台打印输出信息

**console.dir()**可以显示一个对象的所有属性和方法

**prompt(info)**	浏览器弹出输入框，给用户输入	得出的数据类型是String



isNaN本意是通过Number方法把参数转换成数字类型，转换成功则返回false，否则返回true

Number.isNaN判断一个值是否严格等于NaN，会先判断传入的值是否为数字类型



只要有字符串类型和其他类型拼接，最终结果还是字符串型。

**undefined**跟**数字**相加，结果为**NaN**；**null**跟**数字**相加，结果为**数字**。

NaN表示的是非数字, 但是这个非数字也是不同的；因此 NaN 不等于 NaN，两个NaN永远不可能相等



## null和undefined

null表示一个变量被定义了，值是空值

undefined表示一个变量声明了但未定义



## 判断是否为非数字

1. isNaN(n)
2. Object.is(a,b)
3. arr.includes(NaN)
4. 利用NaN自身不相等的特性判断是不是NaN（NaN != NaN）



**typeof**+变量：判断变量类型

“JavaScript有9种数据类型，分别为字符串(**String**)、数字(**Number**)、布尔(**Boolean**)、空(**Null**)、未定义(**Undefined**)、**Symbol**、对象(**Object**)、数组(**Array**)、函数(**Function**)。”



 a++和++a的区别是：a++是使用的a后，再对a进行加1。++a是先把a加1，然后再使用a。 



- 基础数据类型

- 引用数据类型
  -  在内存中表现为一段连续的内存地址 
  - 其简单属性放在栈中
  - 其复杂属性放在堆中



## 变量转为字符型

1. toString()
2. String(变量)
3. 变量+””
4. JSON.stringify()

之间的区别为：

- string是js的全局对象，可以把null，undefined转换成字符
- toString不能转换null，undefined，而且会报错
- JSON.stringify遇到值为undefined、function、symbol会自动忽略该属性，在数组则返回null
- JSON.stringify的结果包含冒号



JSON.stringify原理：

1. 如果目标对象有toJSON()方法，则会执行该方法并返回该方法返回的结果

   ```
       const obj = {
         name:'sdfsd',
         age:undefined,
         toJSON:function(){
           console.log('hahaha')
           return 'hahaha'
         }
       }
       console.log(JSON.stringify(obj))
       --------------------------------
       'hahaha'
   ```

2. Boolean、Number、String对象在字符串化过程中会转换成对应的原始值

   ```
       const obj = {
         name: new String('hahaha'),
         age: new Number(18),
         isBoy: new Boolean(false)
       }
       console.log(JSON.stringify(obj))
       --------------------------------------
       {"name":"hahaha","age":18,"isBoy":false}
   ```

3. undefined、function不是有效的JSON值，如果在转换的过程中遇到此类值，则会被忽略

   ```
       const obj = {
         name:'sdfsd',
         age:undefined
       }
       console.log(JSON.stringify(obj))
       --------------------------------
       {"name":"sdfsd"}
   ```

4. 所有的symbol-key都会被忽略

   ```
       var obj = {}
       obj[Symbol('name')] = 'hhh'
       obj[Symbol('age')] = '18'
       console.log(obj)
       console.log(JSON.stringify(obj))
       ---------------------------------
       {Symbol(name): 'hhh', Symbol(age): '18'}
       {}
   ```

5. 数字 Infinity 和 NaN 以及 null 值都被认为是 null

   ```
       let obj = {
         x:Infinity,
         y:null,
         z:NaN
       }
       console.log(JSON.stringify(obj))
       ------------------------------------
       {"x":null,"y":null,"z":null}
   ```

6. 所有其他 Object 实例（包括 Map、Set、WeakMap 和 WeakSet）将仅序列化其可枚举的属性

7. 时间类型序列化之后变成字符串



## 变量转为数字型

**Number(String)**转为数值型	(后面跟有字符则为非数字)		String-0/String)*1/String-String

**parseInt(String)**转为**整数**（把一个n进制的数转换成十进制的数）

parseFloat(String)**转为**浮点数**	( 此函数确定指定字符串中的第一个字符是否为数字（除空白外）。如果是，它会解析字符串直到到达数字的末尾，并将数字作为数字而不是字符串返回。否则返回NaN)

```
  var a = parseFloat("10")	// 10
  var b = parseFloat("10.00")	// 10
  var c = parseFloat("10.33")	// 10.33
  var d = parseFloat("34 45 66")	// 34
  var e = parseFloat("   60   ")	// 60
  var f = parseFloat("40 years")	// 40
  var g = parseFloat("He was 40")	// 	NaN
```



parseInt方法接收两个参数

1. parseInt的第二个参数radix在(2，36)之间时，如果string参数的第一个字符（除空白以外），不属于radix指定进制下的字符，解析结果为NaN，当radix为0时，ECMAScript5将string作为十进制数字的字符串解析。
2. 当string的数字大于等于radix时，它会解析到string的上一位，并且不再继续解析下一位，如果没有上一位则返回NaN



js在一下场景会自动将数值转换成科学计数法：

1. 当整数的位数超过22位时（1000000000000000000000 => 1e+21）
2. 小数点前边是0，小数点后十分位（包含十分位）之后的0的个数超过6个数值就会自动转化成科学计数法（0.0000004 => 4e-7），0.100000004和1.0000004不会被转换



Number.EPSILON：是JavaScript表示的最小精度

Number.isfinite：检测一个数值是否为有限数

Number.isinteger：判断一个属是否为整数

Math.trunc：将数字的小数部分去除

Math.sign：判断一个数是正数、负数还是0（1，0，-1）

js中数字的最大值：2^53



## 变量转为布尔型

Boolean()		(只有””,0,NaN,null,undefined为false，其他都为true， ’0‘为true)



# 运算符

==：值相等，类型可不等

===：值相等，类型也得相等

- 运算符优先级
  - 小括号>一元运算符（++，--，！）>算术运算符（先*/%后+-）>关系运算符>相等运算符>逻辑运算符（先&&再||）>赋值运算符>逗号
  - ![1629710890315](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1629710890315.png)



二进制否运算符（~）

js将所有的运算子都转成32位二进制整数再进行运算

所有的位运算只对整数有效，当位运算遇到小数时只保留整数部分然后进行运算

一个数与自身的取反值相加等于-1



空值合并运算符（？？）

```
result = (a !== null && a !== undefined) ? a : b;
```



# 隐式转换

-  复杂数据类型在隐式转换时会先转成String，然后再转成Number运算 (对象toString()结果为“[object Object]”)	//.valueOf.()toString()（valueOf获取对象原始值，valueOf为对象再调用toString）
- 字符串连接符+：会把其他数据类型调用String()方法转成字符串然后拼接
- 算术运算符+：会把其他数据类型调用Number()方法转成数字然后做加法运算
-  关系运算符（<、>、<=、>=）：会把其他数据类型转换成number之后再比较关系 
  - 当关系运算符两边有一边是数值的时候，会将其他数据类型使用Number()转换，然后比较关系。
  - 当关系运算符两边都是字符串的时候，从左到右一个一个字符进行比较。
  - 如果一个操作值是对象，则调用valueof方法（没有valueof的话则用toString方法），再进行比较
  - 如果一个操作值是布尔值，则将其转换为数值，再进行比较
-  逻辑运算符（!、&&、||）：会把其他数据类型调用Boolean()方法转成boolean类型
-  乘除、减号、取模运算符（*、/、-、%）：如果操作符之一不是数值，则会被隐式调用Number()函数进行转换
-  相等运算符：类似于关系运算符
- 引用类型数据存在堆中，栈中存储的是地址。



加法运算：

```mermaid
graph LR;
		B(d)-->C[是否都为原始值]
		C-->|是|D[原始值]
		C-->|否|E[对象]
		D[原始值]-->|是字符串|F[字符串相加]
		D[原始值]-->|不是字符串|G[字符串相加]
		E[对象]-->|valueof|H[s]
		H[s]-->|toString|I[s]
		H[s]-->|为原始值|C[是否都为原始值]
		I[s]-->|不为原始值|J[报错]
		I[s]-->|为原始值|C[是否都为原始值]
```





# 分号

分号表示一条语句的结束。Javascript允许省略行尾的分号。

不使用分号的情况

1. for和while循环
2. 分支语句if、try、switch
3. 函数声明语句

- 如果下一行的开始可以与本行的结尾连在一起解释，Javascript就不会自动添加分号
- 只有下一行的开始与本行的结尾无法一起解释，Javascript引擎才会自动添加分号
- 如果一行的起首是自增后者自减运算符，则它们的前面会自动添加分号
- 如果continue、break、return和throw这四个语句后面，直接跟换行符，则会自动添加分号。

立即执行函数前面加上!的原因：将执行!后面的代码，避免上一句表达式没加分号引来的问题



## 单选框多选框

单选框多选框如果不修改value值，则他们获取的value值永远都是on，因为input标签没有设置value属性的值，默认的值就是on。



# 数组

**object instanceof constructor**		instanceof 运算符用于检测**构造函数的属性是否出现在某个实例对象的原型链上**。

**push(参数)**	**末尾添加**一个或者多个元素，返回新的长度

**pop()**	**删除**数组**最后一个元素**，长度减1，返回删除元素的值

**unshift(参数)**	数组开头添加一个或者多个元素，返回新的长度

**shift()**	删除数组的第一个元素，长度减1，返回第一个元素的值

**reverse()**	颠倒数组元素的顺序，影响原数组

**sort()**	数组元素按照转换为的字符串的各个字符的Unicode位点进行排序，影响原数组(x-y是升序)

-  数量小于10的数组使用 InsertionSort，比10大的数组则使用 QuickSort 

**indexOf()**	查找给定元素的第一个索引，存在返回索引号，不存在返回-1。

**lastIndexOf()**	查找数组最后一个元素的索引，存在返回索引号，不存在返回-1。

**toString()**	把数组转换成字符串，用逗号隔开，不影响原数组

**join(‘分隔符’)**	把数组元素转换成字符串，用分隔符隔开，不影响原数组

**concat()**	连接两个或者多个数组，返回新数组，不影响原数组

**slice()**	数组截取slice(begin,end),返回被截取部分，不影响原数组

**splice()**	数组删除(第几个开始，删除的个数)，影响原数组（第三个参数开始之后的参数是添加的）

**flat(Infinity)**	将数组扁平化，不写Infinity的话默认扁平一层

**Array.from(伪数组,加工函数)**		 将一个类数组对象或者可遍历对象转换成一个真正的数组 

**Array.findIndex()**找出第一个符合条件的数组成员的位置，没有则返回-1

**Includes(元素)**		表示某个数组是否包含给定的数值，**返回布尔值**

Indexof跟includes区别：
看一个函数，先看他们的返回值，一个是返回数值型的，一个是返回布尔型的，所以在if条件判断的时候includes要简单得多，而indexOf 需要多写一个条件进行判断。
如果数组中有NaN，你又正好需要判断数组是否有存在NaN，这时你使用indexOf是无法判断的，你必须使用includes这个方法。
当数组的有空的值的时候，includes会认为空的值是undefined，而indexOf不会。



**map(callback[, thisArg])**

callback函数的执行规则

currentValue(当前被传递的元素);index(当前被传递的元素的索引);array(调用map方法的数组)



**arr.reduce(callback(accumulator, currentValue,[currentindex],[sourcearray])**

Accumulator (acc) (累计器)

Current Value (cur) (当前值)

Current Index (idx) (当前索引)

Source Array (src) (源数组)



# 字符串

字符串不能随意改动，改动字符串等同于开辟一块新内存，往新内存放入改动的元素，然后变量指向新内存。

**charAt(index)**	返回指定位置的字符

**charCodeAt(index)**	返回指定位置字符的ASCII码（ 返回值<=255时为英文，当返回值>255时为中文 ； 一个中文占两个字节，一个英文占一个字节 ）

**String.fromCodePoint(num,……)**  返回使用指定的代码点序列创建的字符串

**concat()**	连接两个或者多个字符串，返回新字符串，不影响原字符串

**substr(start,length)**	从start位置开始，取length个数

**slice(start,end)**	从start位置开始，截取到end位置，end取不到

**substring(start,end)**	从start位置开始，截取到end位置，end取不到,不接受负值(若有负值则替换成0)



> slice和substring区别：当接收的参数是负数时，slice会将它字符串的长度与对应的负数相加，结果作为参数；substring则干脆将负参数都直接转换为0



**replace(被替换字符，替换字符)**	替换字符，只替换第一个

|   字符   |         替换文本         |
| :------: | :----------------------: |
|    $&    |    与正则相匹配的文本    |
|    $`    | 匹配到的字符串左边的字符 |
|    $'    | 匹配到的字符串右边的字符 |
| $1,$2... | 匹配结果中对应的分配结果 |

```
'abc'.replace(/b/, "$&123") // 'abc123'
'abc'.replace(/b/, "$`") // 'aac'
'abc'.replace(/b/, "$'") // 'acc'
'aabbcc'.replace(/(a)/, '$1zzz') // 'azzzabbcc'
'sjn@163.com'.replace(/(.+)(@)(.*)/,"$2$1") // '@sjn'
```

回调函数

| 参数索引 | 参数含义                                                   |
| -------- | ---------------------------------------------------------- |
| 0        | 匹配到的字符串                                             |
| 1~n-2    | 正则使用了分组匹配则为多个匹配到的具体字符串，否则无此参数 |
| 3        | 匹配到的字符串的索引                                       |
| 4        | 原始字符串                                                 |

**split(分隔符)**		把字符串转换成数组，用分隔符隔开。

**toUpperCase()**		转换大写

**toLowerCase()**		转换小写

**trim()**			去除字符串两边空格

**toFixed(n)**		保留n位小数

**startsWith(‘str’)**	表示参数字符串是否在原字符串的头部，返回布尔值

**endsWith(‘str’)**	表示参数字符串是否在原字符串的尾部，返回布尔值

**repeat**(n)		将原字符串重复n次，返回一个新字符串	

**indexOf('str')**	返回字符在字符串中的索引，若字符为空，则返回0

**padStart(length,str)**  将指定字符填充到字符串头部，返回新字符串



## 模板字符串

- 模版字符串，用`（反引号）标识，用${}将变量括起来

- 在${}中的大括号里可以放入任意的JavaScript表达式，还可以进行运算

- 模版字符串还可以调用函数

- 如果使用模版字符串表示多行字符串，所有的空格和缩进都会被保存在输出中！

- 函数名称后面跟着模板字符串时，该模板字符串为调用函数所对应的参数，模板字符串有变量时，将模板字符串处理成多个参数后再调用函数；变量替换只发生在数组的第一个成员与第二个成员之间、第二个成员与第三个成员之间，以此类推。

  ```
  tag`Hello ${ a + b } world ${ a * b }`;
  // 等同于
  tag(['Hello ', '', ' world ', ''], 15, 50);
  ```

  

## switch

就是当条件成立了一个后，如果没有break
就会忽略后面的条件case ，把所有的语句都执行了



## unicode

1. 使用*<u>\uxxxx</u>*形式表示一个字符，xxxx表示字符的unicode码点
2. 码点只限于\u0000~\uFFFF之间的字符，超出的话则要用两个字节的形式表示
3. 如果直接在\u后面跟上超过\uFFFF的数值（比如\u20BB7）,js会理解为\u20BB+7，由于\u20BB是一个不可打印字符，则只会显示一个空格且后面跟着个7
4. 将码点放入大括号，能够正确解读字符（比如\u{20BB7}）
5. js允许字符串直接输入字符或者字符的转义形式（比如\u20BB）



# 定时器

**创建定时器**

1. setTimeout（function(){},Timeout）
2. setInterval（function(){},Interval）

**清除定时器**( 获取定时器返回值后，调用clearTimeout(返回值)/clearInterval(返回值), 即可停止计时器 )

1. clearTimeout（timer）
2. clearInterval（timer）

 **定时器的返回值是一个整型的标识。**

- 定时器的第三个参数为定时器回调函数的参数



W3C在HTML标准中规定，规定要求setTimeout中低于4ms的时间间隔算为4ms。

 

# arguments

不确定形参的个数时用arguments来获取。
arguments是伪数组，有length属性，有索引，但没有push、pop等方法。

参数变量和 arguments 是双向绑定的



# 作用域

js引擎运行js分为两步：预解析、代码执行。
预解析：js引擎把js里面所有的var和function提升到当前作用域的最前面（函数的提升快于变量的提升）

```
优点：
1、容错性好。代码在执行前，需要先进行预解析，提前发现一些语法上的错误，及时抛出错误，容错性更好
2、提升性能。预编译时，会统计声明了哪些变量、创建了哪些函数，并对函数的代码进行压缩，去除注释、不必要的空白等。这样的好处就是每次执行函数时都可以直接为该函数分配栈空间（不需要再解析一遍去获取代码中声明了哪些变量，创建了哪些函数）
```

变量的提升：不提升赋值操作，函数的提升：提升函数内容不调用函数。（声明式函数可以先后定义，赋值式函数只能先定义）



作用域从使用方面来解释，作用域就是变量的可访问性，也就是作用域决定了代码中的变量和其他资源在程序的可见性。从存储方面来解释，作用域本质上是一个对象，作用域的变量可以理解成是该对象的成员。



1.全局作用域

- 全局作用域在页面打开时被创建,页面关闭时被销毁
- 编写在script标签中的变量和函数,作用域为全局，在页面的任意位置都可以访问到
- 在全局作用域中有全局对象window,代表一个浏览器窗口,由浏览器创建,可以直接调用
- 全局作用域中声明的变量和函数会作为window对象的属性和方法保存

2.函数作用域:

- 调用函数时,函数作用域被创建,函数执行完毕,函数作用域被销毁
- 每调用一次函数就会创建一个新的函数作用域,他们之间是相互独立的
- 在函数作用域中可以访问到全局作用域的变量,在函数外无法访问到函数作用域内的变量
- 在函数作用域中访问变量、函数时,会先在自身作用域中寻找,若没有找到,则会到函数的上一级作用域中寻找,一直到全局作用域
- 在函数作用域中,不使用变量关键字声明的变量,在赋值时会往上一级作用域寻找已经声明的同名变量,直到全局作用域时还没找到,则会成为window的属性 
- 在函数中定义形参,等同于声明变量 

作用域链

​	一般情况下，变量取值到创建这个变量的函数作用域中取值。但是如果在当前作用域中没有查到值，就会向上级作用域去查，直到查到全局作用域，这么一个查找过程形成的链条就叫做作用域链。



# 闭包

闭包是指有权访问另一个函数作用域中变量的函数 

产生时间：在嵌套函数内部定义执行完时就产生了

死亡时间：在嵌套的内部函数成为垃圾对象时，也就是包含闭包的函数对象成垃圾对象时（f=null）



# 如何判断数据的类型

arr instanceof Array（arr:实例对象，Array:构造函数）

instanceof用于测试构造函数的 prototype 属性是否出现在对象实例原型链中的任何位置

Constructor：arr.constructor == Array

Object.prototype.toString.call() 返回一个形如 "[object xxx]"的字符串。



# 对象



## 创建对象

用字面量创建对象	var obj={键：值,}

用new Object创建对象	var obj=new Object()

用构造函数创建对象
function 构造函数名(){
This.属性=值;
This.方法=function(){};
}
new 构造函数名()；



箭头函数没有prototype、this，因此不能new一个箭头函数



**new Object性能比字面量创建对象差的原因**

{} 是字面量，可以立即求值，而 new Object() 本质上是方法（只不过这个方法是内置的）调用，既然是方法调用，就涉及到在proto链中遍历该方法，当找到该方法后，又会生产方法调用必须的堆栈信息，方法调用结束后，还要释放该堆栈



## 访问对象

在对象中，属性名永远都是字符串。如果使用非字符串（string）的其他值作为属性名，都会转化成string类型，即使数字也不例外。 

点运算符会被优先识别为数字常量的一部分，然后才是对象属性访问符。

[]操作符可以用变量来访问属性名，点操作符不能

[]操作符能用数值访问属性，点操作符不能。

**使用[]的时机：**

1. 属性名包含特殊字符
2. 变量名不确定

对象定义时属性前加#，表示该属性为私有属性，外部不可获取



## 对象方法

object.create(obj)	创建obj对象的原型对象，使用现有的对象来提供新创建的对象的__proto

Object.keys(obj)	获取对象自身所有的键名 ，返回的是一个数组

Object.values(obj)	获取对象所有的键对应的值,会过滤掉属性名为symbol值的属性

Object.entires() 返回一个键值对数组

```
const obj = { foo: 'bar', baz: 42 };
Object.entries(obj)
// [ ["foo", "bar"], ["baz", 42] ]
```

Object.fromEntires()	将一个键值对数组转成对象

```
Object.fromEntries([
  ['foo', 'bar'],
  ['baz', 42]
])
// { foo: "bar", baz: 42 }
```

Object.hasOwnProperty(obj,'attribute')判断对象中是否有某个属性，只会遍历当前对象属性不会判断原型中的属性。

Object.getOwnPropertyNames(obj)返回一个指定对象的属性名组成的数组，包括不可枚举属性

Object.getPrototypeOf()返回一个对象的原型

"x" in obj        in 关键字和hasOwnProperty不同就是 in 关键字会通过原型链一层层往上找直到找到该属性或者到原型链最顶端。



## es6新增方法

Object.is(a,b)	比较a和b是否严格相等，与（===）基本一致，不同之处为：+0不等于-0，NaN等于自身



## new执行时的流程

1、创造一个空对象
2、新对象的_proto_属性指向构造函数的prototype对象
3、把构造函数的this指向新对象
4、返回这个新对象

如果构造函数内部有return语句，而且return后面跟着一个对象，new命令会返回return语句指定的对象；否则，就会不管return语句，返回this对象

如果对普通函数（内部没有this关键字的函数）使用new命令，则会返回一个空对象。



## 控制对象状态

Object.preventExtensions：阻止为添加新的属性对象

Object.seal：阻止为对象添加新的属性的同时页无法删除旧属性（不影响修改属性值）

Object.freeze：阻止为一个对象添加新属性、删除旧属性、修改属性值



## 实例对象

new命令的作用，就是执行构造函数，返回一个实例对象。

new命令会执行构造函数，因此后面的构造函数可以不加括号

构造函数忘记加new时构造函数就变成了普通函数，并不会生成实例对象（解决方法：构造函数内部使用严格模式）

函数内部可以使用new.target属性，倘若函数为new命令调用的则指向当前函数，否则为undefined

当构造函数return了新的数据且在实例化构造函数时，返回非对象类型将不生效



## this注意事项

1. 避免函数的多层嵌套
2. 避免数组处理方法中的this





# 原型链

由构造函数prototype原型对象通过__proto__连接组成的一条指针链路就指原型链
构造函数通过原型分配的函数是所有对象所共享的，每一个构造函数都有一个prototype属性。对象都有一个属性__proto__指向构造函数的protptype原型对象。对象原型和构造函数原型对象都有一个constructor属性。

- 原型对象函数里面的this指向实例对象。
- 所有函数都是Function的实例
- 函数的prototype属性是在定义函数时自动添加的，默认值是一个空的Object对象
- 对象的__proto__属性在创建对象的时候自动添加的，默认值是构造函数的prototype属性值



设置原型对象：Object.setPrototypeOf(obj1,obj2) // 设置obj1的原型对象为obj2

获取原型对象：Object.getPrototypeOf(obj) // 获取obj的原型对象



原型： 原型对象就相当于一个公共的区域，所有同一个类的实例都可以访问到这个原型对象。我们可以将对象中共有的内容，统一设置到原型对象中。 

当我们访问对象的一个属性或方法时,它会先在对象自身中寻找,如果有则直接使用,如果没有则会去原型对象中寻找,如果找到则直接使用。
以后我们创建构造函数时,可以将这些对象共有的属性和方法,统一添加到构造函数的原型对象中,
这样不用分别为每一个对象添加,也不会影响到全局作用域,就可以使每个对象都具有这些属性和方法


# this绑定优先级
1、默认绑定window
2、隐式绑定高于默认绑定
3、显式绑定高于隐式绑定（bind、call、apply）
4、new高于显式绑定


# 改变this

使用call()方法，就会改变this的指向，call的作用就是把obj1的方法放到obj2上使用。

call里面的参数依次为待被指向的对象，调用函数的参数

call()还能实现继承				Function son(a,b,c){Father.call(this,a,b,c)}

```
Function.prototype.mycall = function(context) {
            if (typeof this !== 'function') {
                throw new TypeError('Error')
            }
            context = context || window
            context.fn = this
            let arg = [...arguments].slice(1)
            const result = context.fn(...arg)
            delete context.fn
            return result
        }
```

apply()	数组形式传参	

```
Function.prototype.myapply = function(context) {
            if (typeof this !== 'function') {
                throw new TypeError('Error')
            }
            context = context || window
            let arg = [...arguments[1]]
            context.fn = this
            const result = context.fn(...arg)
            delete context.fn
            return result
        }
```

bind()	不会调用原来的函数

```
Function.prototype.mybind = function(context) {
            if (typeof this !== 'function') {
                throw new TypeError('Error')
            }
            let _this = this
            let arg = [...arguments].slice(1)
            return function F() {
                return _this.apply(context, arg.concat(...arguments))
            }
        }
```

赋值操作等同于反向指向。



# class

1. es6的类，完全是构造函数的另外一种体现

   ```
   class Point {
     // ...
   }
   
   typeof Point // "function"
   Point === Point.prototype.constructor // true
   ```

2. 类的所有方法都定义在类的prototype属性上面



## constructor

1. constructor是类的默认方法，在new命令生成对象实例时，自动调用该方法。
2. 一个类必须要有constructor方法，倘若没有显式定义，则会自动添加一个空的constructor方法
3. constructor方法默认返回实例对象（this），也可以自定义返回一个对象



## 静态方法

1. 静态方法不会被实例继承，而是直接通过类来调用
2. 静态方法的this指向的是类，而不是实例
3. 静态方法可以与非静态方法重名
4. 父类的静态方法可以被子类继承



# 柯里化

作用： 把接收多个参数的函数变换成接收一个单一参数的函数 

- 限制参数的柯里化

  ```
          let sum = (a, b, c, d) => {
              return a + b + c + d
          }
  
          // 柯里化函数，返回一个被处理过的函数 
          let curry = (fn, ...arr) => { // arr 记录已有参数
              return (...args) => { // args 接收新参数
                  if (fn.length <= [...arr, ...args].length) { // 参数够时，触发执行
                      return fn(...arr, ...args)
                  } else { // 继续添加参数
                      return curry(fn, [...arr, ...args])
                  }
              }
          }
          console.log(curry(sum, 1, 2, 3, 4)());
  ```

- 不限制参数的柯里化

  ```
          function text(...arr) {
              return arr.reduce((acc, item) => {
                  return acc + item
              }, 0)
          }
          var sum = (fn, ...arr) => {
              return (...arg) => {
                  if (arg.length === 0) {
                      return fn(...arr, ...arg)
                  } else {
                      return sum(fn, ...arr, ...arg)
                  }
              }
          }
          console.log(sum(text, 1, 2)(2)(3)(4)());
  ```

优点：

1.  参数复用 
2.  延迟执行 



# 遍历

for循序的执行顺序：设置循环变量(var i = 0) ==》循环判断(i<3) ==》满足执行循环体 ==》循环变量自增(i++) 

```
{
  //我是父作用域
  var i = 0;
  if (0 < 3) {
    a[0] = function () {
      //我是子作用域
      console.log(i);
    };
  };
  i++; //为1
  if (1 < 3) {
    a[1] = function () {
      console.log(i);
    };
  };
  i++; //为2
  if (2 < 3) {
    a[2] = function () {
      console.log(i);
    };
  };
  i++; //为3
  // 跳出循环
}
```

for(var i in arr)	遍历数组arr，i为键名

for in会遍历数组所有的可枚举的属性，包括原型的属性。

for(var i of arr)	遍历数组arr，i为键值

[ ].forEach(function(value,index,array){});
forEach方法中的function回调有三个参数：第一个参数是遍历的数组内容，第二个参数是对应的数组索引，第三个参数是数组本身。

filter(function(value,index,arr/){})		查找满足条件的元素并返回数组
some(function(value,index,arr/){})		查找满足条件的元素是否存在并返回布尔值，如果该函数对任意一项返回true,则返回true

every(function(value,index,arr/){})		查找满足条件的元素是否存在并返回布尔值，如果该函数对每一项都返回true，则返回true





中断具体的循环：使用标签来标识循环，然后使用break或者continue语句来中断后者继续执行具体的循环

```
let i, j;

loop1:
for (i = 0; i < 3; i++) {      //The first for statement is labeled "loop1"
  loop2:
  for (j = 0; j < 3; j++) {   //The second for statement is labeled "loop2"
    if (i === 1 && j === 1) {
      continue loop1;
    }
    console.log(`i = ${i}, j = ${j}`);
  }
}

// Output is:
//   "i = 0, j = 0"
//   "i = 0, j = 1"
//   "i = 0, j = 2"
//   "i = 1, j = 0"
//   "i = 2, j = 0"
//   "i = 2, j = 1"
//   "i = 2, j = 2"
```



# Object.defineProperty

Object.defineProperty(obj, prop, descriptor)定义新属性或修改原有的属性
**obj**:要定义属性的对象。
**prop**:要定义或修改的属性的名称或 Symbol 。
**descriptor**:要定义或修改的属性描述符。（对象形式书写{}）
	configurable：当前对象元素的属性描述符是否可改，是否可删除。默认为 false。（为false时下列属性都不可以被修改）
	enumerable：当前对象元素是否可枚举。默认为 false。(在他的父元素被遍历时不可被枚举)
	value：该属性对应的值。可以是任何有效的 JavaScript 值（数值，对象，函数等）。默认为 undefined。
	writable：当且仅当该属性的 writable 键值为 true 时， value才能被赋值运算符改变。默认为 false。
	get：读取元素属性值时的操作
	set：修改元素属性值时的操作



# 严格模式

’use strict’

 类和模块的内部，默认就是严格模式 

**作用**：消除Javascript语法的一些不合理、不严谨之处， 保证代码运行的安全。

严格模式下全局作用域的this为undefined
定时器的this还是指向window
构造函数不加new调用，this会报错（因为this为undefined，不能往undefined添加属性）

**严格模式的限制**

1. 不允许使用未声明的变量
2. 不允许删除变量和对象
3. 不允许变量重名
4. 不允许使用八进制
5. 不允许使用转义字符
6.  变量名不能使用 "arguments" 字符串 



# 浅拷贝

object.assign(target,sources)
浅拷贝只是复制一层，深层的东西则只引用地址。

因为浅拷贝只会将对象的各个可枚举属性进行依次复制，并不会进行递归复制。（不拷贝继承属性）

当我们把一个对象赋值给一个新的变量时，赋的其实是该对象的在栈中的地址，而不是堆中的数据。浅拷贝只复制指向某个对象的指针，而不复制对象本身，新旧对象还是共享同一块内存。但深拷贝会另外创造一个一模一样的对象，新对象跟原对象不共享内存，修改新对象不会改到原对象。

object.assign方法用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target）。
object.assign方法的第一个参数是目标对象，后面的参数都是源对象。(如果目标对象与源对象有同名属性，或多个源对象有同名属性，则后面的属性会覆盖前面的属性)。

- object.assign如果只有一个参数，则直接返回该对象
- object.assign如果参数不是对象，则会先转成对象，再返回
- 如果非对象参数不在首参数，且无法转成参数，就会跳过
- undefined和null为首参数时会报错
- 非对象参数除了字符串其他值都不会产生效果，字符串会以数组的形式拷贝入目标对象
- Object.assign()把数组视为属性名为0，1，2的对象，因此数组合并时会覆盖
- object.assign只能进行值的复制，如果要复制的是一个函数，则会先求函数的返回值再进行复制

```
Object.assign(obj1,obj2)	obj2合并并将obj1覆盖
```



## 深拷贝

1. 使用JSON.parse(JSON.stringify(obj))将对象序列化后又反序列化



# promise

promise主要用于处理异步操作的结果

**promise的状态**

- pending: 初始状态，不是成功或失败状态。 （不会触发then和catch ）
- fulfilled: 意味着操作成功完成。（ 触发then ）
- rejected: 意味着操作失败。（ 触发catch ）

promise如果没有resolve或者reject的话，会还是在pending状态

 **Promise 优缺点**

- 有了 Promise 对象，就可以将异步操作以同步操作的流程表达出来，使得控制异步操作更加容易，而且避免了层层嵌套的回调函数。

- Promise 也有一些缺点。首先，无法取消 Promise，一旦新建它就会立即执行，无法中途取消。其次，如果不设置回调函数，Promise 内部抛出的错误，不会反应到外部。第三，当处于 Pending 状态时，无法得知目前进展到哪一个阶段（刚刚开始还是即将完成）。

  

Promise.all可以将多个Promise实例包装成一个新的Promise实例。同时，成功和失败的返回值是不同的，成功的时候返回的是一个结果数组，而失败的时候则返回最先被reject失败状态的值。 （ **Promise.all获得的成功结果的数组里面的数据顺序和Promise.all接收到的数组顺序是一致的** ）

```
Promise.all([p1, p2]).then((result) => {
  console.log(result)       
}).catch((error) => {
  console.log(error)
})
```

Promise.race可以将多个Promise实例包装成一个新的Promise实例。Promse.race就是赛跑的意思，意思就是说，Promise.race([p1, p2, p3])里面哪个结果获得的快，就返回那个结果，不管结果本身是成功状态还是失败状态。 

```
Promise.race([p1, p2]).then((result) => {
  console.log(result)
}).catch((error) => {
  console.log(error)  // 打开的是 'failed'
})
```

中断promise链的方法是返回一个pending状态的promise（return new Promise(() => {})）



# async、await

async 是一个修饰符，async 定义的函数会默认的返回一个Promise对象，因此对async函数可以直接进行then操作,返回的值即为then方法的传入函数 

await关键字只能放在async函数内部，await关键字的作用就是获取 Promise中返回的内容，获取的是Promise函数中resolve或者reject的值
如果await 后面并不是一个Promise的返回值，则会按照同步程序返回值处理 ，直接返回对应的值

await后面的代码会相当于promisr.then，只是因为await会阻塞作用域内后面的代码，等到外部的同步代码执行完后再回到async内部继续执行await后面的代码

await前有没有加 return 的效果都是一样的



# 正则表达式

创建正则表达式：

```
var name=new RegExp(/表达式/)
var name=/表达式/
```

参数：

1. 第一个参数是字符串，第二个参数表示正则表达式的修饰符
2. 第一个参数是正则表达式，会返回原有正则表达式
3. 第一个参数是正则对象，第二个参数会替代原有正则表达式的修饰符



正则表达式，要么匹配字符，要么匹配位置



/abc/包含abc即可
/[abc]/包含abc任何一个即可
/[^abc]/不包含abc任何一个即可

## 量词

*相当于>=0 可以出现0次或者很多次
+相当于>=1 可以出现1次或者很多次
？相当于1||0

.	 默认匹配除换行符之外的任何单个字符 

.*	匹配任意字符0次或者多次
.*?	只匹配满足正则的最小字符串
.?	匹配任意字符0或者1次 

x(?:y)	 匹配 x且后面要跟着y

x(?=y)	 匹配'x'仅仅当'x'后面跟着'y'.这种叫做先行断言。 

(?<=y)x	 匹配'x'仅当'x'前面是'y'.这种叫做后行断言。 

x(?!y)	 仅仅当'x'后面不跟着'y'时匹配'x'，这被称为正向否定查找。 

{n}相当于重复n次
{n,}相当于重复大于等于n次
{m,n}相当于重复大于等于m次且小于等于n次
\d	匹配0-9之间任一数字，相当于[0-9]
\D	匹配所有0-9之外任一数字，相当于[^0-9]
\w	匹配任意的字母、数字和下划线，相当于[a-zA-Z0-9_]
\W	匹配所有的字母、数字和下划线以外的字符，相当于[^a-zA-Z0-9_]
\s	匹配空格（包括换行符、制表符、空格符等），相当于[\t\r\n\v\f]
\S	匹配非空格的字符，相当于[^\t\r\n\v\f]

\b	匹配有单词边界的字符

\B    匹配非单词边界的字符

dotall:  用s表示dotAll，以使.可以匹配任意字符



**特殊替换字符**
$& 与正则相匹配的字符串

$` 匹配字符串左边的字符

$’ 匹配字符串右边的字符

$1,$2,$,3,…,$n 匹配结果中对应的分组匹配结果



## 量词

表达式/g		全局匹配，下一次匹配只要剩余位置存在匹配即可
表达式/i		忽略大小写
表达式/gi	全局匹配+忽略大小写

表达式/u	正确处理UTF-16编码

表达式/y	全局匹配，后一次匹配要从上一次匹配的下一个位置开始(对match和replace只能返回第一个)



## test

test()	测试字符串是否匹配正则表达式

RegExp.test(str)



## exec

exec() 方法用于检索字符串中的正则表达式的匹配。 

-  命名分组：(?<name>expr) 
- 当正则表达式有g修饰符时，此函数一般会和lastIndex属性匹配使用，此函数会在lastIndex属性指定的字符处开始检索字符串 
-  如果没有找到匹配的字符串，那么返回null，否则将返回一个数组，数组的第0个元素存储的是匹配字符串，第1个到第n个元素存放的是第一个引用型分组(子表达式)匹配的字符串， 
-  exec永远只返回第一个匹配



## exec和match的区别

1. exec是正则表达式的方法，match是字符串提供的方法
2. exec永远只返回第一个匹配，match在/g时会返回所有的匹配



# var,let,const

var有预解析，变量提升；只有函数才会限定作用域

- 变量没有用 var 声明，会被自动提升到全局作用域，因为var声明的变量不支持块级作用域，该变量会向上冒泡到支持的作用域范围（if产生的是一个块级作用域）
- 使用let关键字声明的变量具有块级作用域，没有变量提升，具有暂时性死区，不可以重定义但可以重新赋值变量
- 使用const关键字声明的变量具有块级作用域，声明常量时必须赋值，赋值后值不能改。（不能改变其内存地址）常量	可以在他的基础上添加或者删除
- ES6允许从数组中提取值，按照对应位置，对变量赋值。
- 使用var或者function会创建全局对象属性，也就是（window.a）
- es6允许块级作用域的任意嵌套

```
{{{{
  {let insane = 'Hello World'}
  console.log(insane); // 报错
}}}};
```



三者的区别：

1. 在顶层，var是在全局对象创建一个属性
3. var可以在一个范围内重新声明
4. 用var声明的变量是函数作用域的，let和const声明的变量是块级作用域



let、const声明的变量会提升到块的顶部

从块顶部到该变量的初始化语句，这块区域叫做TDZ（暂时性死区）



## 函数

函数的声明方式

1. 声明式定义函数：function a (){console.log(_)}
2. 函数赋值表达式定义函数：var a = function(){console.log(_)}



用括号包裹定义函数体，解析器将会以函数表达式的方式去调用定义函数，也就是将函数变成一个函数表达式的做法，使解析器正确的调用定义函数。（在函数前加一个!亦是如此）



# 箭头函数()=>{}

1.  箭头函数表达式的语法比函数表达式更简洁，并且没有自己的this，arguments，super或new.target。箭头函数表达式更适用于那些本来需要匿名函数的地方，并且它不能用作构造函数。 
2. 若函数体只有一句代码且为函数返回值，函数体大括号可以省略
3. 如果直接返回一个对象，必须在对象外面加上括号
4. 若形参只有一个，形参外侧的小括号可以去掉
5. 箭头函数不绑定this，箭头函数中的this指向函数所在的作用域指向的对象
6.  箭头函数中的this只在定义的时候绑定，任何方法都改不了箭头函数的this，包括(call、bind、apply)



## 函数声明

1. es5规定函数只能在顶层作用域和函数作用域中声明，不能在块级作用域中声明

2. es6允许在块级作用域中声明函数，但是在块级作用域之外不可引用

3. if内声明的函数会被提升到函数作用域头部

4. es6的块级作用域必须有大括号，否则js引擎认为不存在块级作用域

   ```
   // 第一种写法，报错
   if (true) let x = 1;
   
   // 第二种写法，不报错
   if (true) {
     let x = 1;
   }
   ```

   

5. 



## 函数参数默认值

1. 参数变量是默认声明的，不能使用let或者const再次声明

   ```
   function(a){
   	var a //默认声明
   }
   ```

2. 使用参数默认值时，函数不能有同名参数

   ```
   // 不报错
   function foo(x, x, y){}
   // 报错
   function foo(x, x, y = 1)
   ```

3. 非尾部参数设置默认值，实际上这个参数是无法省略的

4. 如果传入undefined，将触发该参数等于默认值（只有undefined才会触发）

5. 函数的length属性返回的数默认值前面的参数个数

6. 如果设置了参数的默认值，函数初始化时参数会形成一个单独的作用域，进行参数的赋值

7. bind返回的函数，name属性值会加上bound前缀



# 展开运算符

- 用于数组的合并
- 把伪数组变成真正的数组

```
var a=[1,2] var b=[3,4] var c=[...a,...b]	(1,2,3,4)
var a={name:haha,age:18} var b={sex:’女’} var c={...a,...b}  (name:haha,age:18,sex:’女’)
```

#### rest

- 用于获取函数的实参
- rest参数返回的是一个数组
- rest参数必须放在参数最后面
- 用“ ...name ”表示

**解构赋值**

- 数组的结构赋值跟顺序有关系，对象的结构赋值跟顺序没有关系
- 默认值想生效的话，对象与之对应的属性值一定要是underfined
- 非尾部参数设置默认值时，这个参数是无法省略的
- 展开语法和 [`Object.assign()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/assign) 行为一致, 执行的都是浅拷贝(只遍历一层)
- 倘若参数为...objects，则该参数相当于rest（剩余参数）
- 只有函数调用时，扩展运算符才可以放在圆括号中
- 扩展运算符用于数组赋值时，只能放在参数最后一位，否则将会报错
- 对象的解构赋值可以取到继承的属性
- null和undefined无法转成对象，因此无法对他们进行解构赋值
- 解构赋值时等号右边为数值或者布尔值，则会先转为对象

```
({ name: people.name, age: people.age} = result);
```



# Set数据结构

数组中有重复的会去重

- add(value)	添加某个值，返回Set结构本身
- delete(value)	删除某个值，返回一个布尔值，表示删除是否成功
- has(value)	返回一个布尔值，表示该值是否为Set的成员
- clear()	清空所有成员，没有返回值



set认为NaN和NaN是相等的

set判断两个值是否相同使用的是类似于（===）



## Map数据结构

map对象保存键值对，任何值都可以作为一个键或者一个值，构造函数可以接受一个数组作为参数

size属性：返回map对象中所包含的键值对的个数

方法：

- set(key, val): 向Map中添加新元素
- get(key): 通过键值查找特定的数值并返回
- has(key): 判断Map对象中是否有Key所对应的值，有返回true,否则返回false
- delete(key): 通过键值从Map中移除对应的数据
- clear(): 将这个Map中的所有元素删除



遍历方法：

- `keys()`：返回键名的遍历器
- `values()`：返回键值的遍历器
- `entries()`：返回键值对的遍历器
- `forEach()`：使用回调函数遍历每个成员



综上所述，主要有一下几个**区别**：

1.Map是键值对，Set是值的集合，当然键和值可以是任何的值；

2.Map可以通过get方法获取值，而set不能因为它只有值；

3.都能通过迭代器进行for...of遍历；

4.Set的值是唯一的可以做数组去重，Map由于没有格式限制，可以做数据存储

5.map和set都是stl中的关联容器，map以键值对的形式存储，key=value组成pair，是一组映射关系。set只有值，可以认为只有一个数据，并且set中元素不可以重复且自动排序。



## symbol

1. Symbol函数前不能使用new命令，因为生成的Symbol是一个原始类型的值，不是对象
2. 如果Symbol的参数是一个对象，就会调用该对象的toString方法，将其转成字符串，然后才生成一个Symbol值
3. Symbol函数的参数只是表示对当前Symbol值的描述，因此相同参数的Symbol函数的返回值是不相等的
4. Symbol值不能与其他类型的值进行运算，但只可显式转为字符串和布尔值
5. Symbol值作为属性名时，不能使用点运算符，因为点运算符后面跟着的时字符串
6. 由于Symbol值作为属性名，不能被常规的方法遍历得到，所以可以给对象定义一些内部方法和属性



属性:

1. description	返回Symbol的描述



# Event loop

包含一个函数执行栈、一个宏任务队列和一个微任务队列。

执行宏任务时，先在队列中只取一个来执行，当这个宏任务执行完后，会进入到一个时间间隙，也就是两个宏任务之间存在一个微任务队列，然后将微任务队列的所有任务都执行完，再执行下一个宏任务。

在调度一个宏任务之前，先查看微任务队列是否有任务，有则先执行完微任务队列的所有任务再执行宏任务



# 浏览器eventloop跟node的eventloop区别

1.浏览器的Event Loop和Node.js的Event Loop是不同的，实现机制也不一样，不要混为一谈。
2.Node.js 可以理解成有4个宏任务队列和2个微任务队列，但是执行宏任务时有6个阶段。
3.Node.js中，先执行全局Script代码，执行完同步代码调用栈清空后，先从微任务队列Next Tick Queue中依次取出所有的任务放入调用栈中执行，再从微任务队列Other Microtask Queue中依次取出所有的任务放入调用栈中执行。然后开始宏任务的6个阶段，每个阶段都将该宏任务队列中的所有任务都取出来执行（注意，这里和浏览器不一样，浏览器只取一个），每个宏任务阶段执行完毕后，开始执行微任务，再开始执行下一阶段宏任务，以此构成事件循环。
4.MacroTask包括：setTimeout、setlnterval、setlmmediate（Node）、requestAnimation（浏览器）、
lO、UI rendering
5.Microtask包括：process.nextTick（Node）、Promise.then、Object.observe、MutationObserver




# 函数防抖（debounce）

当持续触发事件时，一定时间段内没有再触发事件，事件处理函数才会执行一次，如果设定的时间到来之前，又一次触发了事件，就重新开始延时。

```
var timer=null 
btn.onclick=function（）{
    c1earTimeout（timer）
    timer=setTimeout（（）=>{
    	console.1og（’发送请求了?’）
    }，1000）
}
```



# 函数节流（throttle）

当持续触发事件时，保证一定时间段内只调用一次事件处理函数。

```
var flag=true 
btn.onclick=function（）{
    if（flag）{
        flag=false 
        console.log（’发送请求.’）
        setTimeout（（）=>{
            flag=true
        }，1000）
    }
}
```



## requestAnimationFrame

该方法可以在下一帧开始时调用指定函数，将所有DOM操作集中起来，在一次重绘或者回流中完成，并且重绘或者回流的时间间隔紧紧跟随着浏览器的刷新频率。



defer：延迟脚本。立即下载，但延迟执行（延迟到整个页面都解析完毕后再运行），按照脚本出现的先后顺序执行。
async：异步脚本。下载完立即执行，但不保证按照脚本出现的先后顺序执行。





## navigator

该属性指向一个包含浏览器和系统信息的 Navigator 对象。脚本通过这个属性了解用户的环境信息。

##### 属性

1. navigator.userAgent：返回用户的设备信息（浏览器的产商、版本、操作系统等）
2. navigator.platform：返回用户的操作系统
3. navigator.onLine：返回布尔值表示用户当前在线还是离线（浏览器短线）
4. 用户变成在线触发online事件，变成离线触发offline事件
5. navigator.connection：返回一个包含当前网络连接的相关信息



## screen

screen.orientation：返回一个对象，表示屏幕的方向,type表示具体方向

1. landscape-primary：横放
2. landscape--secondary：颠倒的横放
3. portrait-primary：表示颠倒的横放
4. portrait-secondary：表示颠倒的竖放



# cookie

1. Cookie 是服务器保存在浏览器的一小段文本信息，一般大小不能超过4KB。浏览器每次向服务器发出请求，就会自动附上这段信息。
2. Cookie 的目的就是区分用户，以及放置状态信息
3. 单个域名设置的cookie不应超过30个，每个cookie的大小不能超过4kb
4. 区分cookie时不考虑协议和端口
5. http回应可以包含 多个Set-Cookie字段，即在浏览器生成多个cookie
6. 如果要修改设置过的cookie，则需要将cookie的key、domain、path、secure都要一致，否则会生成一个全新的cookie，下次访问时浏览器向服务器发送两个同名的cookie



## export和export default同时存在

同时存在的话，引入的时候 export加{}，而export default可定义为随便一个名称

export default在同一个文件中只可存在一个



## 垃圾回收机制

1. 标记清除

   mark阶段将可达的数据进行标记

   sweep阶段将没有标记到的数据进行回收

   缺点：清理内存后内存是不连续的，导致内存碎片化严重，可能会导致大对象不能找到可利用空间的问题

   这里所谓的清除并不是真的置空，而是把需要清除的对象地址保存在空闲的地址列表里。下次有新对象需要加载时，判断垃圾的位置空间是否够，如果够，就存放。

2. 引用计数

   标记每个变量呗引用的次数，为0时才释放这块内存。

   当有一个值不再需要时，引用数却不为0，垃圾回收机制无法释放这块内存



## audio

volume：设置并返回音频的音量（0 - 1）



## MutationObserver

功能：监听DOM的变化

```
const observer = new MutationObserver(callback);
const options = {}
const a = document.querySelector('#app')
observer.observer(a, options)
```



## width（都是只读属性）

1. offsetWidth：包含元素可见宽度，padding，border（包含滚动条）
2. clientWidth：包含元素可见宽度，padding（不包含滚动条）
3. scrollWidth：元素内容高度，包括由于溢出导致视图中不可见的内容，padding（不包括滚动条）
4. offsetWidth、clientWidth、scrollWidth属性值会被四舍五入为一个整数，如果需要小数值的话，可使用element.getBoundingClientRect()
5. window.innerWidth：窗口的文档显示区的宽度
6. window.outerWidth：窗口的外部宽度，包含工具条，F12



## getBoundingClientRect

返回一个DOMRect对象，如下：（根据视口左上角来计算的（0，0））

```
top: 元素上边距离视口上边的距离
left: 元素右边距离视口左边的距离
right: 元素右边距离视口左边的距离
bottom: 元素下边距离视口上边的距离
width: 元素宽度
height: 元素高度
```

