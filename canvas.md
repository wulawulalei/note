## canvas（画布）

canvas是 HTML5 新增的元素，可用于通过使用JavaScript中的脚本来绘制图形例如，它可以用于绘制图形，创建动画。<canvas> 最早由Apple引入WebKit



## 替换内容

IE9之前的浏览器不支持元素“canvas”

支持<canvas>的浏览器将会忽略在容器中包含的内容，并且只是正常渲染canvas。
不支持<canvas>的浏览器会显示代替内容



## canvas标签的两个属性

- canvas元素默认具有宽高

  ```
  width:300px;
  height:150px;
  ```

- html属性设置width height时只影响画布本身不影画布内容
- css属性设置width height时不但会影响画布本身的高宽，还会使画布中的内容等比例缩放（缩放参照于画布默认的尺寸）



## 渲染上下文

canvas元素只是创造了一个固定大小的画布，要想在它上面去绘制内容，我们需要找到它的渲染上下文

canvas元素有一个叫做 getContext() 的方法，这个方法是用来获得渲染上下文和它的绘画功能。getContext()只有一个参数，上下文的格式

- 获取方式

  ```
  var canvas = document.getElementById('box');
  var ctx = canvas.getContext('2d');
  ```

- 检查支持性

  ```
  var canvas = document.getElementById('tutorial');
  if (canvas.getContext){
     var ctx = canvas.getContext('2d');
  } 
  ```

  

## 绘制矩形

- 1px变2px原因

   这是由于绘制时，将画笔中线对齐坐标轴线，必然有一半线宽在坐标轴线之外，这一半的线宽，如果不是整数，会被自动加满，使之正好对齐一个像素点，由于本身是不满这1个像素的，所以用了更浅的颜色来表示（改变透明度），导致模糊。（因为1像素就是最小单位了，0.x的像素不能显示） 

  - 当绘制方向上的坐标是整数时

    - 若线宽为奇数，那么无论如何，线条的矩形区域都坐标都多出0.5像素，于是补满，整体多出了1像素。
    - 若线宽为偶数，那么无论如何，画笔中线总是对齐坐标的，线条宽度不会产生偏差。
    - 若当线宽为小数，那么无论如何，线条的矩形区域都坐标都存在小数，于是补满。整体也会多出1像素。

- 三种方法绘制矩形
  绘制一个填充的矩形（填充色默认为黑色）

  ```
  fillRect(x, y, width, height)
  ```

  绘制一个矩形的边框（默认边框为:一像素实心黑色）

  ```
  strokeRect(x, y, width, height)
  ```
  
    清除指定矩形区域，让清除部分完全透明。（画了一个跟画布背景一摸一样的矩形）
  
  ```
  clearRect(x, y, width, height)
  ```
- 添加样式和颜色
   fillStyle：设置图形的填充颜色。
   strokeStyle：设置图形轮廓的颜色。默认情况下，线条和填充颜色都是黑色
   lineWidth：这个属性设置当前绘线的粗细。属性值必须为正数。

- 设定线条与线条间接合处的样式（lineJoin，默认是 miter）
        round : 圆角
        bevel : 斜角
        miter : 直角

## 绘制路径

- 步骤
  	1.首先，你需要创建路径起始点。
   2.然后你使用画图命令去画出路径
   3.之后你把路径封闭。
   4.一旦路径生成，你就能通过描边或填充路径区域来渲染图形。

```
beginPath()新建一条路径，生成之后，图形绘制命令被指向到路径上准备生成路径。（清空路径容器）

moveTo(x, y)将笔触移动到指定的坐标x以及y上，当canvas初始化或者beginPath()调用后，通常会使用moveTo()函数设置起点

lineTo(x, y)将笔触移动到指定的坐标x以及y上，绘制一条从当前位置到指定x以及y位置的直线。

closePath()闭合路径之后图形绘制命令又重新指向到上下文中。如果图形是已经闭合了的，即当前点为开始点，该函数什么也不做。

stroke()通过线条来绘制图形轮廓。不会自动调用closePath()

fill()通过填充路径的内容区域生成实心的图形。自动调用closePath()

rect(x, y, width, height)绘制一个左上角坐标为（x,y），宽高为width以及height的矩形。当该方法执行的时候，moveTo()方法自动设置坐标参数（0,0）。也就是说，当前笔触自动重置会默认坐标

arc(x, y, radius, startAngle, endAngle, anticlockwise)，画一个以（x,y）为圆心的以radius为半径的圆弧（圆），从startAngle开始到endAngle结束，按照anticlockwise给定的方向（默认为顺时针）来生成。
ture：逆时针；false:顺时针

arcTo(x1, y1, x2, y2, radius)，根据“开始点”、“控制点”和“结束点”这三个点所形成的夹角，然后绘制一段与夹角的两边相切并且半径为radius的圆弧。弧线的起点是“开始点所在边与圆的切点”，弧线的终点是“结束点所在边与圆的切点”。

quadraticCurveTo(cp1x, cp1y, x, y)，绘制二次贝塞尔曲线，cp1x,cp1y为一个控制点，x,y为结束点。起始点为moveto时指定的点。

bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)，绘制三次贝塞尔曲线，cp1x,cp1y为控制点一，cp2x,cp2y为控制点二，x,y为结束点。起始点为moveto时指定的点。

drawImage(img,startX,startY,endX,endY)绘制图片

getImageData（startX,startY,width,height）获取像素点数据
```



## 变换（可累加）

- translate(x, y)：用来移动 canvas的原点到一个不同的位置。
  translate 方法接受两个参数。x 是左右偏移量，y 是上下偏移量，

- rotate(angle)：旋转canvas的坐标轴

  顺时针方向的，以弧度为单位的值。旋转的中心点始终是 canvas 的原点。

- scale(x, y)：放大或者缩小canvas画布里面css像素的面积
  	x,y 分别是横轴和纵轴的缩放因子，它们都必须是正值。
  	缩放一般我们用它来增减图形在 canvas 中的像素数目，对形状，位图进行缩小或者放大。



## 存储状态

- save() 是 Canvas 2D API 通过将当前状态放入栈中，保存 canvas 全部状态的方法
- restore() 是 Canvas 2D API 通过在绘图状态栈中弹出顶端的状态，用顶端的状态将当前的状态覆盖









# echarts

- 鼠标经过的样式：emphasis
- 坐标轴：axisLine
- 坐标轴刻度：axisTick
- echarts图标的位置和大小：grid
- 调色盘：color
- 鼠标经过后的提示：tooltip
- 图标的标题：title
- 图标的颜色解析：legend