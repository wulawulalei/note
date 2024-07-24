Pointer-events:none;该元素不能被点击
"--name：n" 的属性，然后使用 var(‘--name’) 函数调用该属性：



## 字体属性（font）

font-style:字体样式(倾斜是italic)(不倾斜是normal)

font-weight:字体粗细(加粗=700/bold)(normal/400)

font-size:字号(px)

font-family:字体

font:字体连写(字号，字体必须同时出现)



## 文本装饰(test)

text-align:对齐方式

text-decoration:（underlline:下划线,overline:上划线，line-through:删除线，none:取消下划线）

text-indent:文本第一行首行缩进的距离。(em:一个文字大小距离。)

line-height:行间距

Letter-spacing:字间距



## 选择器

标签选择器：选出所有相同的标签

类选择器（.类名）：选取一个或者多个标签

id选择器（#id名）：只能选择一个标签

通配符选择器（*）：选取页面所有标签

复合选择器：（权重会叠加）

后代选择器：爷 子 孙{}（空格隔开）

子元素选择器：父>子{}（>号隔开）

并集选择器：1,2,3{}（逗号隔开）

**链接伪类选择器**：（必须按照顺序写选择器，不然没有效果）

1.未访问的链接(a:link)

2.点击过的链接(a:visited)

3.鼠标经过的那个链接(a:hover)

4.鼠标正在按下还没有弹起鼠标的那个链接(a:active)

**Focus伪类选择器**：元素:focus{}

把获得光标的input表单元素选取出来(input:focus)	获取焦点

**选择器优先级**：

- !important（1，0，0，0，0）
- 行内样式（1，0，0，0）
- id选择器（0，1，0，0）
- 类选择器、伪类选择器、属性选择器（0，0，1，0）
- 元素选择器和伪元素（0，0，0，1）
- 通配符选择器（0，0，0，0）



A+B:选择紧接在A后的一个B元素

A~B:查找A后B的所有节点



## 背景

背景颜色：background-color

背景图片：background-image:url(路径)

背景平铺：backgroud-repeat： (repeat:背景图像在纵向横向都平铺	no-repeat:背景图像不平铺	repeat-x:背景图像在横向平铺	repeat-y:背景图像在纵向平铺)

背景图片位置：position:top|center|bottom|left|center|right

背景图像固定：background-attachment:(scroll:背景图像随对象内容滚动	fixed:背景图像固定)

背景色半透明：background:rgba(0,0,0,x);

背景色渐变:background: -webkit-linear-gradient(起始位置 ,起始颜色,终止颜色);

```
background: -webkit-gradient(to left, from(#36aafd), color-stop(20%, #0077ff));
// 从开始位置为#36aafd色，从0%-20%逐渐渐变成#0077ff，从20%开始到结束位置都为#0077ff
```

渐变色在CSS中被定义成了 image 类型，因此在background-color和color中使用无效，

倒影：-webkit-box-reflect：direction offset color
above：指定倒影在对象的上边
below：指定倒影在对象的下边
left：指定倒影在对象的左边
right：指定倒影在对象的右边
offset：倒影与对象之间的间隔，可以为负值。
另外还可以使用渐变以及图片。

background-size:背景图片宽度，背景图片高度
单位：长度|百分比|cover|contain
cover把背景图像扩展至足够大，以便背景图像完全覆盖背景区域

contain把背景图像扩展至最大尺寸，以便其宽度和高度完全适应内容区域

透明度：opacity: value（规定不透明度。从 0.0 （完全透明）到 1.0（完全不透明））|inherit;



## clip-path

作用：裁剪出所需要的形状（数值可为百分比）

圆形：circle(半径at圆心坐标)

椭圆形：ellipse（长、短轴半径t圆心坐标）

内置矩形：inset（上右下左的边距round上右下左圆角）

其他：polygon(坐标点，坐标点)



## BFC（块级格式化上下文）

定义：一个BFC区域包含创建该上下文元素中的所有子元素，但是不包括子元素中的子元素。BFC是一块独立的渲染区域，不同的BFC区域之间是相互独立的，互不影响的。



生成BFC的方法：

1. 设置浮动，不包括none
2. 设置定位，包括absolute，fixed
3. 设置overflow，包括hidden，auto，scroll
4. 行内快显示模式，即inline-block
5. 表格单元格，即table-ceil



作用：

1. 解决外边距塌陷问题
2. 解决包含塌陷（子元素margin影响到父元素）
3. 清除浮动
4. 阻止标准流元素被浮动元素覆盖



## 盒子

边框宽度：border-width

边框样式：border-style(solid:实线边框；dashed:虚线边框；datted:点线边框)

边框颜色：border-color

圆角边框：border-radius:

盒子大小为宽度*高度：box-sizing:border-box(padding和margin不会撑开盒子)

内边距：padding(上，右，下，左)

margin/padding设置百分比是相对于父盒子的width而言的

如果盒子本身没有指定width/height属性，则此时padding不会撑开盒子。

外边距:margin(上，右，下，左)

块级盒子水平居中：盒子必须指定宽度，并且左右外边距都设置为auto.

行内元素或者行内块元素水平居中给其父元素添加text-align:center即可。

行内元素只能设置左右外边距，没有大小。行内元素添加绝对/固定定位，可以直接给宽度和高度。



## 阴影

盒子阴影：box-shadow:h-shadow v-shadow blur(模糊距离) spread(阴影尺寸) color insert

文字阴影：text-shadow:h-shadow v-shadow blur(模糊距离) color（水平，垂直）

往右的阴影 / 往下的阴影 / 模糊程度 / 模糊距离

inset表示向内部的阴影模糊度



## 高度塌陷问题

（1）产生的原因：1.在文档流中，父元素的高度默认被子元素撑开
                                  2.当子元素浮动脱离文档流，无法继续撑起父元素高度，导致父元素塌陷。
嵌套块元素垂直外边距的塌陷解决方案：

1.为父元素定义边框

2.为父元素定义内边距

3.为父元素添加overflow:hidden（能清除块内子元素的浮动影响. 因为该属性进行超出隐藏时需要计算盒子内所有元素的高度, 所以会隐式清除浮动）



## 垂直外边距的重叠问题

(1)产生的条件：1.网页中垂直方向的相邻的外边距会产生外边距的重叠

(2)产生的问题: 1.兄弟元素之间相邻的外边距会取最大值（而不是求和）

​                               2.父子元素之间的垂直外边距相邻了,子元素的外边距设置值会传给父元素。

解决的方法：

- 在父元素使用before伪类选中最前面的部分，为空白快，显示为table标签，使其与子元素隔开，

使其不相邻，阻止了外边距的重叠，就不会导致子元素外边距传递给父元素。

- 子元素添加浮动。

脱标的盒子不会触发外边距塌陷



## 浮动(float)

添加浮动后元素具有行内块的特性。

浮动不会影响前面的标准流。

浮动元素只会压住下面的标准流盒子，不会压住标准流盒子里面的文字或者图片。



## 清除浮动

- 额外标签法(在最后一个浮动的子元素后面添加一个额外标签，添加清除模式(clear:both))
- 父级添加overflow:overflow:hidden
- 添加after伪元素:ie6,7版本浏览器不支持伪元素；使用zoom:1触发hasLayout.
- 使用before和after双伪元素清除浮动：使用zoom:1触发hasLayout.

```
.clearfix:after,.clearfix:before{
        content: "";
        display: table;
    }
    .clearfix:after{
        clear: both;
    }
    .clearfix{
        *zoom: 1;
    }
```



## 定位(position)			

z-index 属性设置元素的堆叠顺序。Z-index 仅能在定位元素上生效，除了静态定位(static)
静态定位(static)：类似于标准流

层叠等级：层叠上下文根元素<定位并且z-index:<0<块级元素<浮动元素<定位并且z-index:auto/0<定位并且z-index:>>0



### 相对定位(relative)

1.他是相对于自己原来的位置来移动的

2.原来在标准流的位置继续占有



### 绝对定位(absolute)

1.如果没有祖先元素或者祖先没有定位，则以浏览器为准定位。

2.如果祖先元素有定位(相对，绝对，固定定位)，则以最近一级有定位的祖先元素为参考点移动位置。

3.绝对定位不再占有原先的位置。



### 固定定位(fixed)：

1.以浏览器的可视窗口为参照点移动元素

2.固定定位不占有原先的位置



### 粘性定位(sticky)：

1.以浏览器的可视窗口为参照点移动元素

2.粘性定位占有原先的位置



## 元素的显示和隐藏

display:block/none(隐藏时不再占有位置)

Visiibility:visible/hidden(隐藏时占有位置)



## 元素溢出(overflow)

auto:在需要时剪切内容并添加滚动条。

scroll:总是显示滚动条。

hidden:不显示超过对象尺寸的内容。



## 鼠标样式（cursor）

default:默认样式

pointer:小手

move:移动

text:文本

not-allowed:禁止



## 元素垂直对齐方式（只针对行内元素和行内块元素）

加在img上
vertical-align:	元素放在父元素基线上(默认)

vertical-align:top 把元素的顶端与行中最高元素的顶端对齐

vertical-align:middle 元素放在父元素的中部

vertical-align:bottom 把元素的底端与行中最高元素的底端对齐



- 图片在div中底部会有空白：因为图片默认的vertical-align为baseline，所以会有空白



## 单行文本溢出省略号显示

```
overflow:hidden;
white-space:nowrap;
text-overflow:ellipsis;
```



## 多行文本溢出省略号显示

```
overflow:hidden;
text-overflow:ellipsis;
display:-webkit-box;
-webkit-line-clamp:n;
-webkit-box-orient:vertical;
```

p标签自动换行：word-break: break-all



## white-space

1. pre：空白会被浏览器保留，内容未自动换行
2. pre-wrap：保留空白符序列，正常地进行换行
3. pre-line：合并空白符序列，正常地进行换行



## filter过滤器

- filter: grayscale(100%) // 灰度100% 

- filter: blur(5px) // 模糊5px 

- filter: brightness(300%) // 3倍亮度 

- filter: contrast(200%) // 200%对比度 

- filter: saturate(200%) //200%饱和度 

- filter: hue-rotate(180deg) // 色相旋转180度 

- filter: invert(100%) // 100%反色 

- filter: opacity(50%) // 50%透明度 

- filter: drop-shadow(10px 5px 5px #f00) // 阴影 

- filter: sepia(70%)  // 褐色程度70%

   

## 计算属性

calc()					calc(100%-30px)


## 属性选择器

E[att]	选择具有att属性的E元素

E[att=”val”]		选择具有att属性且属性值等于val的E元素

E[att^=”val”]		选择具有att属性且属性值以val开头的E元素

E[att$=”val”]		选择具有att属性且属性值以val结尾的E元素

E[att*=”val”]		选择具有att属性且属性值中含有val的E元素



## 伪类选择器

从第五个开始：n+5		前五个：-n+5

E:nth-child(n)		匹配父元素中的第n个子元素E

E:nth-of-type(n)		指定类型E的第n个



## 2D转换:(transition)

谁做过度给谁加

过度：transition:变化属性 花费时间 运动曲线 何时开始

transform:translate(x,y)/		translateX(n)/		translateY(n)

沿着X和Y轴移动元素；不会影响到其他元素的位置；对行内元素没有效果。

translate参数是带有%，移动的距离是根据盒子自身宽度和高度来对比。

transform:rotate()	绕着中心点旋转

transform:origin:x y		转换旋转点	（x,y可以写像素(px)或者方位名词(left ……)）

transform:scale(x,y)	/	scale(n)	放大缩小(不会影响到其他元素的位置)

transform:skew()		斜切（x:逆时针，y:顺时针）

transform-style:preserve-3d		控制子盒子是否开启3d空间。

透视：在需要透视效果的元素的父类加perspective.

透视就是类似于视距，眼睛到屏幕的距离，距离越小看到的物体越大。

transform 的所有属性都不改变页面元素的布局。最多引起重绘



## 定义动画

@keyframes name{
0% / from{}
100% / to{}
}



## 调用动画

animation-name:(动画名称)

animation-duration:(持续时间)

animation-delay:动画开始时间

animation-iteration-count:动画被播放的次数(infinite 无限)

animation-timing-function:规定动画的速度曲线

animation-direction:动画在下一周期是否逆向播放(alternate  逆播放)

animation-play-state:规定动画是否正在运行或停止(running pause)

animation-fill-mode:动画结束后，保持位置不变(forwards),回到起始位置(backwards)

动画曲线：linear:匀速	ease:低速开始，然后加快，最后减速	steps(n):步长



## 私有前缀

（为了兼容老版本）
-moz-:代表firefox私有属性
-ms-:代表ie浏览器私有属性
-webkit-:代表safari,chrome浏览器私有属性
-o-:代表opera私有属性



## @support

作用：根据浏览器对css特性的支持情况来定义不同的样式

操作符分别有not，and，or，当条件为true时才会执行代码

```
@supports not (display:flex){
	.hhh{
		float:left
	}
}
```



## GPU加速

css中一下几个属性能触发硬件加速：transform、opacity、filter、will-change



## window.print

- 此方法打印的是body的内容
- 如果需要加上背景色或者背景图，则需要加上

```
-webkit-print-color-adjust:exact;
-moz-print-color-adjust:exact;
-ms-print-color-adjust:exact;
print-color-adjust:exact;
```

倘若还不生效，则需要在背景色或者背景图的样式中加上!important



## 文字环绕

shape-outside



## 设置宽高比

```
aspect-ratio: 1 / 1;（宽 / 高）
```



## device-pixel-ratio

```
@mixin hhh($url) {
	@media screen and (-webkit-max-device-pixel-ratio: 2), (max-device-pixel-ratio: 2) {
		background-image: url(#{$url} + '.png');
	}
	@media screen and (-webkit-min-device-pixel-ratio: 2), (min-device-pixel-ratio: 2) {
		background-image: url(#{$url} + '@2x.png');
	}
	@media screen and (-webkit-min-device-pixel-ratio: 3), (min-device-pixel-ratio: 3) {
		background-image: url(#{$url} + '@3x.png');
	}
}

.hhh {
	width: 300px;
	height: 300px;
	@include hhh('/src/assets/logo');
}
```

## flex
**flex-basis** 该属性用来设置元素的宽度，通常情况下 flex 布局的默认主轴方向为 row (行)，此时大家使用 width 设置宽度。但是如果元素上同时设置了 width 和 flex-basis ，那么 width 的值就会被 flex-basis 覆盖掉。
**flex-grow** 该属性用来设置当父元素的宽度大于所有子元素的宽度的和时（即父元素会有剩余空间），子元素如何分配父元素的剩余空间。 flex-grow 的默认值为 0，意思是该元素不索取父元素的剩余空间，如果值大于0，表示索取。值越大，索取的越厉害。
```
假如设置父元素 400px，子元素 A 为100px，子元素 B 为 200px.则剩余空间为 100px
例子一：
A的 flex-grow 为 0，B的 flex-grow 为 0（即A、B不设置该属性）
则A、B的实际宽度为他们本身的宽度，即A的实际宽度为100px  ； B的实际宽度为200px
例子二：
A的 flex-grow 为1，B的 flex-grow为0（即不设置该属性）
则A的实际宽度为 100px + 100px =200px    ；  B的实际宽度为 200px + 0 = 200px
例子三：
A的 flex-grow 为 1，B的 flex-grow 为 2
则 A 的实际宽度为 100px + 100px * 1/3 =  400/3 px  , B的实际宽度为 200px + 100px * 2/3 = 800/3 px 
上面的 总系数为 1 + 2 = 3 ，然后按照 各元素的 flex-grow 的属性值进行分配 A 1/3   B 2/3
```
**flex-shrink** 该属性用来设置子元素的 缩小比例，当父元素的宽度小于所有子元素的宽度的和时（即子元素会超出父元素），子元素如何缩小自己的宽度的。 flex-shrink 的默认值为 1，当父元素的宽度小于所有子元素的宽度的和时，子元素的宽度会减小。值越大，减小的越厉害。如果值为 0，表示不减小。
```
假如设置父元素 400px，子元素A为 200px，子元素B为 300px.则超出空间为 100px
例子一：
设置A的 flex-shrink 为 0，B的 flex-shrink 为 0
则A，B都不减小宽度，A、B的实际宽度为他们本身的宽度，即A的实际宽度为 200px  ； B的实际宽度为 300px 
例子二：
A的 flex-shrink 为 0，B的 flex-shrink 为 1，则A不减小宽度，B减小
则A的实际宽度为他本身的宽度= 200px   ， B的实际宽度为 300px - 100px（超出的宽度）= 200px
例子三：
如果A，B都减小宽度，A设置 flex-shirk 为 3，B设置 flex-shirk 为 2。则最终 A 的大小为 自身宽度 (200px) - A减小的宽度(100px * (200px * 3 / (200px * 3 + 300px * 2))) = 150px
最终 B 的大小为 自身宽度 (300px)- B减小的宽度 (100px * (300px * 2/(200px* 3 + 300px* 2))) = 250px
```
