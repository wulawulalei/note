# 变量

**alert(msg)**	浏览器弹出警示框

**console.log(msg)**	浏览器控制台打印输出信息

**console.dir()**可以显示一个对象的所有属性和方法

**prompt(info)**	浏览器弹出输入框，给用户输入	得出的数据类型是String



**isNaN()** 判断非数字，是数字返回false，否则返回true。

只要有字符串类型和其他类型拼接，最终结果还是字符串型。

**undefined**跟**数字**相加，结果为**NaN**；**null**跟**数字**相加，结果为**数字**。



**typeof**+变量：判断变量类型

“JavaScript有9种数据类型，分别为字符串(**String**)、数字(**Number**)、布尔(**Boolean**)、空(**Null**)、未定义(**Undefined**)、**Symbol**、对象(**Object**)、数组(**Array**)、函数(**Function**)。”



 a++和++a的区别是：a++是使用的a后，再对a进行加1。++a是先把a加1，然后再使用a。 



- 基础数据类型

- 引用数据类型
  -  在内存中表现为一段连续的内存地址 
  - 其简单属性放在栈中
  - 其复杂属性放在堆中



## 变量转为字符型

变量.toString()	/	String(变量)	/	变量+””



## 变量转为数字型

**Number(String)**转为数值型	(后面跟有字符则为非数字)		String-0/String)*1/String-String

**parseInt(String)**转为**整数**	**parseFloat(String)**转为**浮点数**	(后面跟有字符则去掉字符)
parseInt方法接收两个参数
parseInt的第一个参数radix为0时，ECMAScript5将string作为十进制数字的字符串解析；
parseInt的第二个参数radix在2—36之间时，如果string参数的第一个字符（除空白以外），不属于radix指定进制下的字符，解析结果为NaN。

Number.EPSILON：是JavaScript表示的最小精度

Number.isfinite：检测一个数值是否为有限数

Number.isinteger：判断一个属是否为整数

Math.trunc：将数字的小数部分去除

Math.sign：判断一个数是正数、负数还是0（1，0，-1）



## 变量转为布尔型

Boolean()		(只有””,0,NaN,null,undefined为false，其他都为true)



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



# 隐式转换

-  复杂数据类型在隐式转换时会先转成String，然后再转成Number运算 (对象toString()结果为“[object Object]”)	//.valueOf.()toString()
- 字符串连接符+：会把其他数据类型调用String()方法转成字符串然后拼接
- 算术运算符+：会把其他数据类型调用Number()方法转成数字然后做加法运算
-  关系运算符：会把其他数据类型转换成number之后再比较关系 
  - 当关系运算符两边有一边是字符串的时候，会将其他数据类型使用Number()转换，然后比较关系！，十位数或者以上只返回第一个字符的编码。
  - 当关系运算符两边都是字符串的时候，从左到右一个一个字符进行比较。
-  逻辑非运算符：会把其他数据类型调用Boolean()方法转成boolean类型
- 引用类型数据存在堆中，栈中存储的是地址。



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



# 逻辑与短路运算

第一个表达式为真，返回第二个表达式；第一个表达式为假，返回第一个表达式。



# 逻辑或短路运算

第一个表达式为真，返回第一个表达式；第一个表达式为假，返回第二个表达式。



# 三元表达式

条件表达式？表达式1：表达式2



# 数组

**object instanceof constructor**		instanceof 运算符用于检测**构造函数的属性是否出现在某个实例对象的原型链上**。

**push(参数)**	**末尾添加**一个或者多个元素，返回新的长度

**pop()**	**删除**数组**最后一个元素**，长度减1，返回删除元素的值

**unshift(参数)**	数组开头添加一个或者多个元素，返回新的长度

**shift()**	删除数组的第一个元素，长度减1，返回第一个元素的值

**reverse()**	颠倒数组元素的顺序，影响原数组

**sort()**	数组元素按照转换为的字符串的各个字符的Unicode位点进行排序，影响原数组

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

**str[index]**	获取指定位置处字符		h5支持

**concat()**	连接两个或者多个字符串，返回新字符串，不影响原字符串

**substr(start,length)**	从start位置开始，取length个数

**slice(start,end)**	从start位置开始，截取到end位置，end取不到

**substring(start,end)**	从start位置开始，截取到end位置，end取不到,不接受负值

**replace(被替换字符，替换字符)**	替换字符，只替换第一个

**split(分隔符)**		把字符串转换成数组，用分隔符隔开。

**toUpperCase()**		转换大写

**toLowerCase()**		转换小写

**trim()**			去除字符串两边空格

**toFixed(n)**		保留n位小数

**startsWith(‘str’)**	表示参数字符串是否在原字符串的头部，返回布尔值

**endsWith(‘str’)**	表示参数字符串是否在原字符串的尾部，返回布尔值

**repeat(n)**		将原字符串重复n次，返回一个新字符串	

indexOf('str')	返回字符在字符串中的索引，若字符为空，则返回0



## 模板字符串

模版字符串，用`（反引号）标识，用${}将变量括起来
在${}中的大括号里可以放入任意的JavaScript表达式，还可以进行运算
模版字符串还可以调用函数
如果使用模版字符串表示多行字符串，所有的空格和缩进都会被保存在输出中！



# 定时器

**创建定时器**

1. setTimeout（function(){},Timeout）
2. setInterval（function(){},Interval）

**清除定时器**( 获取定时器返回值后，调用clearTimeout(返回值)/clearInterval(返回值), 即可停止计时器 )

1. clearTimeout（timer）
2. clearInterval（timer）

 **定时器的返回值是一个整型的标识。**

- 定时器的第三个参数为定时器回调函数的参数

 

# arguments

不确定形参的个数时用arguments来获取。
arguments是伪数组，有length属性，有索引，但没有push、pop等方法。



# 作用域

js引擎运行js分为两步：预解析、代码执行。
预解析：js引擎把js里面所有的var和function提升到当前作用域的最前面
变量的提升：不提升赋值操作，函数的提升：提升函数内容不调用函数。

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

闭包就是能够读取其他函数内部变量的函数。 

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



**new Object性能比字面量创建对象查的原因**

{} 是字面量，可以立即求值，而 new Object() 本质上是方法（只不过这个方法是内置的）调用，既然是方法调用，就涉及到在proto链中遍历该方法，当找到该方法后，又会生产方法调用必须的堆栈信息，方法调用结束后，还要释放该堆栈



## 访问对象

在对象中，属性名永远都是字符串。如果使用非字符串（string）的其他值作为属性名，都会转化成string类型，即使数字也不例外。 

[]操作符可以用变量来访问属性名，点操作符不能

[]操作符能用数值访问属性，点操作符不能。

**使用[]的时机：**

1. 属性名包含特殊字符
2. 变量名不确定

对象定义时属性前加#，表示该属性为私有属性，外部不可获取



## 对象方法

Object.keys(obj)	获取对象自身所有的键名 ，返回的是一个数组

Object.values(obj)	获取对象所有的键对应的值

Object.hasOwnProperty(obj,'attribute')判断对象中是否有某个属性，只会遍历当前对象属性不会判断原型中的属性。

Object.getOwnPropertyNames(obj)返回一个指定对象的属性名组成的数组，包括不可枚举属性

"x" in obj        in 关键字和hasOwnProperty不同就是 in 关键字会通过原型链一层层往上找直到找到该属性或者到原型链最顶端。



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



# 改变this

使用call()方法，就会改变this的指向，call的作用就是把obj1的方法放到obj2上使用。
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

for(var i of arr)	遍历数组arr，i为键值

[ ].forEach(function(value,index,array){});
forEach方法中的function回调有三个参数：第一个参数是遍历的数组内容，第二个参数是对应的数组索引，第三个参数是数组本身。

filter(function(value,index,arr/){})		查找满足条件的元素并返回数组
some(function(value,index,arr/){})		查找满足条件的元素是否存在并返回布尔值



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

因为浅拷贝只会将对象的各个属性进行依次复制，并不会进行递归复制。

当我们把一个对象赋值给一个新的变量时，赋的其实是该对象的在栈中的地址，而不是堆中的数据。浅拷贝只复制指向某个对象的指针，而不复制对象本身，新旧对象还是共享同一块内存。但深拷贝会另外创造一个一模一样的对象，新对象跟原对象不共享内存，修改新对象不会改到原对象。

object.assign方法用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target）。
object.assign方法的第一个参数是目标对象，后面的参数都是源对象。(如果目标对象与源对象有同名属性，或多个源对象有同名属性，则后面的属性会覆盖前面的属性)。

```
Object.assign(obj1,obj2)	obj2合并并将obj1覆盖
```



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

中断promise链的方法是返回一个pending状态的promise



# async、await

async 是一个修饰符，async 定义的函数会默认的返回一个Promise对象，因此对async函数可以直接进行then操作,返回的值即为then方法的传入函数 

await关键字只能放在async函数内部，await关键字的作用就是获取 Promise中返回的内容，获取的是Promise函数中resolve或者reject的值
如果await 后面并不是一个Promise的返回值，则会按照同步程序返回值处理 



# 正则表达式

创建正则表达式：

```
var name=new RegExp(/表达式/)
var name=/表达式/
```

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

(?:x)	 匹配 'x' 但是不记住匹配项 , 没有将此结果进行存储 

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

dotall:  用s表示dotAll，以使.可以匹配任意字符



**特殊替换字符**
$& 与正则相匹配的字符串

$` 匹配字符串左边的字符

$’ 匹配字符串右边的字符

$1,$2,$,3,…,$n 匹配结果中对应的分组匹配结果



## 参数

表达式/g		全局匹配
表达式/i		忽略大小写
表达式/gi	全局匹配+忽略大小写



## test

test()	测试字符串是否匹配正则表达式

RegExp.test(str)



## exec

exec() 方法用于检索字符串中的正则表达式的匹配。 

-  命名分组：(?<name>expr) 
- 当正则表达式有g修饰符时，此函数一般会和lastIndex属性匹配使用，此函数会在lastIndex属性指定的字符处开始检索字符串 
-  如果没有找到匹配的字符串，那么返回null，否则将返回一个数组，数组的第0个元素存储的是匹配字符串，第1个到第n个元素存放的是第一个引用型分组(子表达式)匹配的字符串， 



# var,let,const

var有预解析，变量提升；只有函数才会限定作用域

变量没有用 var 声明，会被自动提升到全局作用域，因为var声明的变量不支持块级作用域，该变量会向上冒泡到支持的作用域范围（if产生的是一个块级作用域）

使用let关键字声明的变量具有块级作用域，没有变量提升，具有暂时性死区，不可以重定义但可以重新赋值 变量
使用const关键字声明的变量具有块级作用域，声明常量时必须赋值，赋值后值不能改。（不能改变其内存地址）常量	可以在他的基础上添加或者删除
ES6允许从数组中提取值，按照对应位置，对变量赋值。\undefined

三者的区别：

1. 在顶层，var是在全局对象创建一个属性
2. var声明的变量会发生变量提升，let和const不会
3. var可以在一个范围内重新声明
4. 用var声明的变量是函数作用域的，let和const声明的变量是块级作用域



# 箭头函数()=>{}

 箭头函数表达式的语法比函数表达式更简洁，并且没有自己的this，arguments，super或new.target。箭头函数表达式更适用于那些本来需要匿名函数的地方，并且它不能用作构造函数。 

若函数体只有一句代码且为函数返回值，函数体大括号可以省略
若形参只有一个，形参外侧的小括号可以去掉
箭头函数不绑定this，箭头函数中的this指向定义时所处的对象



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
- 解构赋值为浅拷贝
- 不能直接输出解构的对象，会报错



# Set数据结构

数组中有重复的会去重
add(value)		添加某个值，返回Set结构本身
delete(value)		删除某个值，返回一个布尔值，表示删除是否成功
has(value)		返回一个布尔值，表示该值是否为Set的成员
clear()			清空所有成员，没有返回值

getComputedStyle(obj, null)[‘name’]	获取obj的name属性



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



# Echars

步骤1：引入echarts.js文件
步骤2：准备一个呈现图表的盒子
步骤3：初始化echarts实例对象
echarts.init(呈现图表的盒子)
步骤4：准备配置项
var option={
//横坐标
xAxis:{
type:'category'，
data:【'小明‘，‘小红’，‘小王】
}，
//纵坐标
yAxis:{
type:‘value'
}，
//数据
series:【
name:‘语文’，
type:'bar'，
data:【7e，92，，87】

步骤5：将配置项设置给echarts实例对象
mCharts.setOption(option)



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



## 垃圾回收机制

1. 标记清除

   mark阶段将可达的数据进行标记

   sweep阶段将没有标记到的数据进行回收

   缺点：清理内存后内存是不连续的，导致内存碎片化严重，可能会导致大对象不能找到可利用空间的问题

   这里所谓的清除并不是真的置空，而是把需要清除的对象地址保存在空闲的地址列表里。下次有新对象需要加载时，判断垃圾的位置空间是否够，如果够，就存放。

2. 引用计数

   标记每个变量呗引用的次数，为0时才释放这块内存。

   当有一个值不再需要时，引用数却不为0，垃圾回收机制无法释放这块内存
