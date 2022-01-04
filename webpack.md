浏览器不能识别less文件以及模块



test：匹配哪些文件

use：使用哪些loader进行处理





style-loader：创建style标签，将js中的样式资源插入执行，添加到head中生效

css-loader：将css文件变成commonjs模块加载到js中，里面的内容是样式字符串

url-loader默认使用es6去解析，html-loader引入图片是使用commonjs

修改图片的名字：name：'[hash:10].[ext]'取图片名字哈希值前十位并使用原有图片后缀



plugins:webpack中要使用的插件

使用插件方法：直接new插件