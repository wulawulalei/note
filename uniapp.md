使用cli脚手架创建的项目跟HBuilderX创建项目的区别

1. cli创建的项目的编译器不会跟随HBuilderX升级，而需要执行npm update或者修改package.json中的依赖版本
2. HBuilderX创建的项目会随着HBuilderX的升级而自动升级编译器



## 引入资源

`@`开头的绝对路径以及相对路径会经过base64转换规则校验

绝对路径：@或者/开头



## 应用生命周期

1. onLaunch:在uniapp初始化完成时触发
2. onShow：在uniapp启动时或者从后台进入到前台时触发
3. onHide：在uniapp从前台到后台时触发

应用生命周期只能在App.vue中监听



## 前后台

- 小程序后台运行一定时间（5分钟）或者系统资源占用过高的话，会被销毁
- 当用户关闭小程序或者离开了微信，小程序并没有被销毁，而是进入了后台，当再次进入小程序时或者再次进入微信时，又会从后台进入到前台



## 自定义导航栏

1. 隐藏原生的navigationBar

   ```
   "navigationBar":"custom"
   ```






## 获取节点

1. uni.createSelectorQuery()	返回一个SelectorQuery对象实例
2. selectorQuery.in(component)    将选择器的选取范围更改为自定义组件component内，返回一个SelectorQuery对象实例





## 拦截器

1. uni.addInterceptor('拦截名称'，拦截回调)
2. uni.removeInterceptor(拦截名称)



## 本地缓存

1. 往本地缓存存储数据：uni.setStorage(object)	uni.setStorageSync(key,data)
2. 往本地缓存获取数据：uni.getSrorage()	uni.getStorageSync()
3. 往本地缓存删除指定key：uni.removeStorage()	uni.removeStorageSync()
4. 清除本地数据缓存：uni.clearStorage()	uni.clearStorageSync()