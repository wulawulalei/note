```
<!DOCTYPE html>:文档类型声明标签告诉页面采取html5版本来显示页面。
```



## 语义化

​	Web语义化是指使用恰当语义的html标签、class类名等内容，让页面具有良好的结构与含义，从而让人和机器

都能快速理解网页内容。语义化的web页面一方面可以让机器在更少的人类干预情况下收集并研究网页的信息，从

而可以读懂网页的内容，然后将收集汇总的信息进行分析，结果为人类所用；另一方面它可以让开发人员读懂结构

和用户以及屏幕阅读器（如果访客有视障）能够读懂内容。




## 文体标签

Html:html文档的跟标签

Head 头标签，指定html文档的一些属性，引入外部的资源

Title 标题标签

Body 文体标签（bgcolor：背景颜色；background：背景图片；text：整片文字颜色（六位二进制数））



## 文本标签

```
<h1>…<h6> 标题
<p> 段落标签
<br> 换行标签
<hr/> 水平线标签 （color=’’ width=’’ align（对齐方式）=’’）
<b> <i> 加粗，斜体标签
```



## 图片标签

<img src='图片路径'> 	

alt 规定图片的替代文本

title  鼠标经过图片的提示文本

./代表当前目录，../代表上一级目录



## 列表标签

有序列表 <ol(type=’’ start=’’)> <li></li>… <li><li/></ol>

无序列表：<ul(type=’’ start=’’)> <li></li>… <li><li/></ul>

去掉前面的符号：list-style:none;



## 链接标签

<a href='网址' target='(_self:在当前页面打开，_blank:在空白页面打开)'></a>
锚点连接：href值(#x)对应的标题的id(x)或者是对应a的name（点击连接会直接滑到对应的地方）
color: inherit;		取消a的默认颜色

块标签：(文字类元素内不能使用块标签)
<span> 

<div> 每一个div沾满一行
## 表格标签：
align:对齐方式
width:表格宽度
cellspacing:定义单元格之间的距离。
<td rowspan:所占行数 colspan:所占列数>
border-collapse:collapse; 表示边框合并在一起。
border-collapse:separate;表示边框之间的间距，间距的大小用border-spacing:px;定义大小。


## 块级标签和行内标签的区别

1.行内元素与块级函数可以相互转换，通过修改display属性值来切换块级元素和行内元素，行内元素display：inline，块级元素display：block。

2.行内元素和其他行内元素都会在一条水平线上排列，都是在同一行的；块级元素却总是会在新的一行开始排列，各个块级元素独占一行，垂直向下排列，若想使其水平方向排序，可使用左右浮动（float：left/right）让其水平方向排列。

3.行内元素不可以设置宽高，宽度高度随文本内容的变化而变化，但是可以设置行高（line-height），同时在设置外边距margin上下无效，左右有效，内填充padding上下无效，左右有效；块级元素可以设置宽高，并且宽度高度以及外边距，内填充都可随意控制。    

4.块级元素可以包含行内元素和块级元素，还可以容纳内联元素和其他元素；行内元素不能包含块级元素，只能容纳文本或者其他行内元素。




## input
<input> 标签规定了用户可以在其中输入数据的输入字段。


### type

password:密码输入框
radio:单选框
checkbox:多选框		发生改变用change事件
1.要想让多个单选框实现单选的效果，则多个单选框的name属性值必须一样。
2.一般给每一个单选框提供value属性，指定其被选中后提交的值。
3.checked属性指定默认值（默认选中）

file:文件选择框
submit:提交按钮，可以提交表单。
button:普通按钮。
image:定义图像作为提交按钮。required=required	表示该内容不能为空

### placeholder

指定输入框的提示信息，当输入框的内容发生变化，会自动清空提示信息。
取消表单轮廓：outline:none
设置按钮不可点击：disabled:false

### autofocus

页面加载完成后自动聚焦到此表单

### autocomplete

当用户在字段开始键入时，浏览器基于之前键入过的值，显示在字段中填写的选项。默认已经打开，需要放在表单内，并且加上name属性和成功提交。
on：打开		off:关闭

### multiple

可以多选文件提交	



## label

<label>:label的for属性会和input的id属性值对应，点击label区域，让input输入框获取焦点。点击label会让所属的单选框被选中。

## form

作用：用于定义表单，定义一个范围用于采集用户数据

action:指定提交数据的URL

method:指定提交方式

- get:
  1. 请求参数会在地址栏中显示，会封装到请求行中
  2. 请求参数大小有限制。
  3. 不太安全

- post:
  1. 请求参数不会在地址栏中显示，会封装到请求体中
  2. 请求参数大小没有限制。
  3. 较为安全

enctype=”multipart/form-data”	将表单数据编码成二进制类型

表单项中的数据要想被提交，必须指定其name属性。



## video

```
<video width=’’ height=’’ ...>
	<source src=’’ type=’video/mp4’></source>
</video>
```

autoplay=autoplay(视频就绪自动播放)

controls=controls(向用户显示播放控件)

loop=loop(循环播放)

preload:规定是否预先加载视频，如果有autoplay属性则忽略此属性

auto:预先加载视频

none:不预先加载视频

poster=图片(加载等待时的图片)

muted=muted(静音播放)



## 像素

默认情况下，移动端的网页都会将视口设置为980像素（css像素）

如果网页宽度超过了980，移动端会自动对网页进行缩放以完整显示网页

浏览器在显示网页时，需要将css像素转换成物理像素然后再呈现

像素比=（css像素：物理像素）

默认情况下，移动端的像素比是视口宽度（980）/设备物理像素

<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0, minimum-scale=1.0, user-scalable=no">
name="viewport"		表示该标签为视口标签
width=device-width	表示布局宽度等于设备宽度
initial-scale=1.0	表示初始缩放比
maximum-scale=1.0	表示最大缩放比
minimum-scale=1.0	表示最小缩放比
user-scalable=no	表示用户是否可以缩放


## 响应式布局

所谓响应式布局，就是指同一个网页，在不同的终端上的显示效果不同，但是访问的确实是同一个页面，只是因为浏览器会根据终端的不同（例如屏幕宽度、横竖屏、移动端还是pc端等）选择的渲染方式也不同。

实现响应式布局：
先做好PC端的样式，然后使用css中的@media媒体查询来适配不同的终端。

清除点击高亮：-webkit-tap-highlight-color:transparent

按钮输入框自定义属性：-webkit-appearance:none

禁用长按页面时的弹出菜单：-webkit-touch-callout:none



## 流式布局（百分比布局）

max-width最大宽度	(max-height最大高度)
min-width最小宽度	(min-height最小高度)

### flex

flex父项属性（display:flex）

flex:增长系数 缩减系数 元素基础长度flex-direction:设置主轴的方向
(row:默认值，从左到右 row-reverse:从右到左	column:从上到下	column-reverse:从下到上)

flex-grow:指定弹性元素的伸展系数

当父元素有多余空间的时，会按照比例进行分配

justify-content:设置主轴上的子元素排列方式
(flex-start:默认值，从头部开始，主轴为x则从左到右	flex-end:从尾部开始排列
center:在主轴居中对齐		space-around:平分剩余空间		space-between:两边贴边再平分剩余空间)

flex-wrap:设置子元素是否换行
(nowrap:默认值，不换行	wrap:换行)

align-content:设置侧轴上的空白的分布
(space-sround:子项在侧轴平分剩余空间	space-between:子项在侧轴两边贴边再平分剩余空间)

align-items:设置侧轴上的子元素的排列方式（单行）
(flex-start:默认值，从上到下	flex-end:从下到上center:在侧轴居中对齐		stretch:拉伸)

flex-flow:复合属性，相当于同时设置了direction和wrap

1rem等于html根元素设定的font-size的px值
1em等于父元素设定的font-size的px值



## 媒体查询

@media 媒体类型 关键字 (媒体特性)
媒体类型(all:所有设备	print:打印机和打印浏览	scree:电脑屏幕，平板电脑，智能手机等)
关键字(and	not	only)

ie9及以下不支持，需添加response.js才可使用



## 栅格系统

屏幕宽度<768px	最大宽度100%	类前缀.col-xs-
屏幕宽度>=768px	最大宽度750px	类前缀.col-sm-
屏幕宽度>=992px	最大宽度970px	类前缀.col-md-
屏幕宽度>=1200px	最大宽度1170px	类前缀.col-lg-
类偏移：类前缀+offset		等同于margin

列排序：类前缀+push/pull	等同于浮动




## window.url

作用：用于同步读取文件的字符串

- URL.createObjectURL(object)	创建一个URL对象，参数为用于创建的File、blob和MediaSource对象，返回object的url地址
- URL.revokeObjectURL(object)    释放URL对象，因为URL对象在document卸载的时候才释放



## fileReader 

作用：用于异步读取文件的字符串

file.onchange(function(){

​	var reader = new FileReader();

​	reader.readAsDataURL(文件);

​	reader.onload = function () {

   	console.log(reader.result); 

​	}

})



## window.url与fileReader的区别

**主要区别**
			通过FileReader.readAsDataURL(file)可以获取一段data:base64的字符串

​	通过URL.createObjectURL(blob)可以获取当前文件的一个内存URL

**执行时机**
			createObjectURL是同步执行（立即的）
			FileReader.readAsDataURL是异步执行（过一段时间）

**内存使用**
			createObjectURL返回一段带hash的url，并且一直存储在内存中，直到document触发了unload事件（例如：document close）或者执行revokeObjectURL来释放。
			FileReader.readAsDataURL则返回包含很多字符的base64，并会比blob url消耗更多内存，但是在不用的时候会自动从内存中清除（通过垃圾回收机制）
兼容性方面两个属性都兼容ie10以上的浏览器。

**优劣对比**
			使用createObjectURL可以节省性能并更快速，只不过需要在不使用的情况下手动释放内存
			如果不太在意设备性能问题，并想获取图片的base64，则推荐使用FileReader.readAsDataURL





## 预加载(<link>)

preload:在浏览器渲染机制之前进行处理资源，而且不会阻塞onload事件，待到需要时自行调用（可加载跨域资源）

preload设置as属性告诉浏览器加载的是什么资源，从而正确的发送accept头部信息，浏览器可以设置正确的资源加载优先级

prefetch:浏览器在空闲时间提前请求资源并且缓存以供后续使用，页面跳转时prefetch请求不会中断（将其放入缓存至少五分钟）



在preload或者prefetch的资源加载时，两者都存储在httpcache,当资源加载完成后，如果资源是可以被缓存的，那么其会在httpcache中等待后续操作，如果资源不可被缓存，那么其在被使用前均存储在memorycache



## svg

(rx ry x-axis-rotation large-arc-flag sweep-flag x y)+

rx ry 是椭圆的两个半轴的长度。

x-axis-rotation 是椭圆相对于坐标系的旋转角度，角度数而非弧度数。

large-arc-flag 是标记绘制大弧(1)还是小弧(0)部分。

sweep-flag 是标记向顺时针(1)还是逆时针(0)方向绘制。

x y 是圆弧终点的坐标。

1. stroke-dasharray：用于创造虚线，值依次是虚线的长度和虚线的间距
2. stroke-dashoffset：相对与起始位置的偏移
3. stroke：线的颜色
4. stroke-width：线的宽度
5. stroke-linecap：线的首尾形状
