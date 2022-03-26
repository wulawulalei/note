浏览器不能识别 less 文件以及模块

test：匹配哪些文件

use：使用哪些 loader 进行处理

style-loader：创建 style 标签，将 js 中的样式资源插入执行，添加到 head 中生效

css-loader：将 css 文件变成 commonjs 模块加载到 js 中，里面的内容是样式字符串

url-loader 默认使用 es6 去解析，html-loader 引入图片是使用 commonjs

修改图片的名字：name：'[hash:10].[ext]'取图片名字哈希值前十位并使用原有图片后缀

plugins:webpack 中要使用的插件

chunks：指定需要插入到文本的 js 文件，对应 entry 中的 key 值，如果只有一个入口文件可以不写这个参数

使用插件方法：直接 new 插件

## source-map

source map 是一个信息文件，里面储存着位置信息，也就是转换后的代码的每一个位置所对应的转换前的位置。当出错的时候，除错工具将直接显示原始代码，而不是转换后的代码。

主要包括以下字段：

1. version: Source Map(源映射)的版本号，目前统一使用版本 3。
2. file: (可选)生成文件的路径(相对于 Source Map(源映射) 本身路径)。
3. names: (可选)所有名称，如变量名、函数名，下文详细介绍。
4. sourceRoot: (可选)所有源文件的根路径(相对于 Source Map(源映射) 本身路径)
5. sources: 所有源文件的路径(相对于 sourceRoot)
6. sourcesContent: (可选)所有源文件的内容。
7. mappings: 所有映射点，表示转换前后代码的位置映射。

mappings:

1. mappings 是一个数组通过编码转换成字符串的，这个数组包含了每一行的映射点列表

   ```
   mappings = [
      第 1 行的映射点列表,
      第 2 行的映射点列表,
      ...
   ]
   ```

2. 每行的映射点又是一个数组，包含了这一行多有列的映射点

   ```
   mappings = [
       [ 第 1 行第 1 个映射点, 第 1 行第 2 个映射点, ... ] // 第 1 行的映射点列表
       [ 第 2 行第 1 个映射点, 第 2 行第 2 个映射点, ... ] // 第 2 行的映射点列表
       ...
   ]
   ```

3. 每个映射点又是一个数组，数组中包含五个数字

   ```
   [ 生成文件的列, 源文件索引, 源文件行号, 源文件列号, 名称索引 ]
   ```

mappings 编码：

1. 计算相对值

   ​ 将映射点中每个数字替换成当前映射点和上一个映射点相应位置的差（省略部分按 0 处理）

2. 合并数字

   ​ 将 mappings 中的所有数字写成一行，不同映射点使用都好隔开，不同行使用分号隔开

3. 编码数字

   ​ 每个数字使用 VLQ 编码将其转为字母

VLQ 编码：

1. 如果数字是负数，则将其取反
2. 将数字转换成二进制数，并在末尾补符号位，负数补 1，整数补 0
3. 从右到左分割二进制数，一次取五位，不足的往前面补 0
4. 分好的二进制数进行倒序
5. 所有的二进制数前面补 1，而最后一个二进制补 0
6. 根据 base64 编码表将二进制数转成字母

源码转换：

1. 压缩、减少体积。
2. 多个文件合并，减少 HTTP 请求数。
3. 其他语言编译成 js。

## chainwebpack 和 configwebpack 区别
1、chainwebpack 通过链式编程的形式，来修改默认的 webpack 配置
2、configwebpack 通过操作对象的形式，来修改默认的 webpack 配置，该对象会被 webpack-merge 合并最终得 webpack 配置


## externals
该配置为打包时忽略掉某些包，但是需要在html页面中引入

## htmlWebpackPlugin
   多页面按需引入资源
    <% if (htmlWebpackPlugin.options.filename == 'index.html') { %>
      当页面名称为index.html时引入的内容
    <% } else { %>
       当页面名称不为index.html时引入的内容
   <% } %>