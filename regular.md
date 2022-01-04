## 创建继承Regualr的组件

继承Regular组件

```
const HelloRegular =  Regular.extend({
	template:`
		hello{username}
	`
})
```

```
const hello = new Regular({
            template: `
            {#if lalala}
                    hello{username}
                {#else}
                    <a href="javascript:;" on-click={this.login()}>sorry,please login</a>
            {/if}
            `,
            data: {
                username: "zhangsan"
            },
            login: function () {
                console.log('hhh');
            }
        })
        hello.$inject('#app')
```



## 传入数据

组件实例的初始化数据通过data属性传入

```
const component=new HelloRegular({
	data:{username:'hhh'}
})
```

- 只有data上的字段可以通过声明式属性传入
- 不要在extend或者implement时定义data，否则data属性的值会共享



## 将组件插入到节点中

使用$inject将组件插入到目标节点的指定位置$inject(node[,direction])

1. bottom：作为node的lastChild插入
2. top：作为node的firstChild插入
3. after：作为node的nextSibling插入
4. before：作为node的previousSibling插入



## 条件语句

```
{#if username}
hello{username}
{#else}
sorry,please login
{/if}
```



## 绑定事件

在节点上声明on-click绑定点击事件



## 组件参数传递

- 传入的属性都会成为data的属性

- 非属性插值传入的属性都为字符串

- 属性插值则会创建双向绑定

- 如果插值表达式为静态值，则不会产生双向绑定

- 若传入的属性没有value值，则默认成为Boolean

- 参数的命名若为连缀格式则自动转为驼峰

  ```
  show-modal 会转换为 showModal
  ```

- 给子组件添加isolate属性可让子组件与父组件完全隔离



## 生命周期

1. config：在模板编译前调用
2. init：在模板编译后调用，可获取到生成的节点，但是还没插入到dom节点中
3. destroy：在组件销毁前调用，需要调用父类(this.super)来销毁一些通用部分(如事件监听，数据监听)
4. modifyBodyComponent



## 模块钩子函数

1. enter：进入路由节点的钩子函数
2. leave：离开路由节点的钩子函数
3. mount：路由参数更新时或者enter时调用钩子函数



所有钩子函数都有跳转参数option和resolve

- option.param：路由参数
- option.current：目标路由节点
- option.previous：跳转前的路由节点
- option.replace：上一个历史记录会被当前替换
- option.encode：若为false，地址的URL不会发生变化，仅仅触发了内部状态的转换



倘若钩子函数声明了resolve参数但是没有调用的话，跳转的内容不展示，且模块钩子函数不执行



## 获取节点

1. 使用ref标记节点，使用this.$refs.name获取节点
2. 使用dom.element()获取组件的子节点，不写true则返回第一个子节点，否则返回子节点数组



## 列表渲染

```
<ul>
	{#list sequence as item}
	<li>{item.name}</li>
	{#else}
	<div>no result</div>
	{/list}
</ul>
```

- 每次迭代会创建一个名为 {别名_index}的下标别名，下标从 0 开始。
- else是为了展示列表为空的情况



## 不支持的表达式

1. 自增自减运算符（++或者--）
2. 位运算符(&或者|)
3. 正则表达式字面量



## 计算属性

直接传入函数，会作为getter函数存在

- get(data)data指向component.data
- set(value,data)value为将要设置的属性值，data为component.data
- 组件的计算字段通过$get('name')获取



## 过滤器

```
Regular.filter({
	'filterName':function(list,split){//list为要过滤的元素，split为过滤需要的元素
		return...
	}
})
new Regular({
	template；·
		<div>{list|join:'+'}</div>
	·
})
```

过滤器的优先级比三元运算符低，可以在外面包裹括号提高优先级

regualr也有双向过滤，通过get和set进行过滤



## 一次性绑定

使用@()可提供一次数据绑定，监视器在一次变更后会被移除

```
<div>{ @(title) }</div> // the interpolation only trigger once

{#if @(test)}  // only test once
//...
{/if}

{#list @(items) as item}  // only trigger once
//...
{/list}

component.$watch("@(user.name)", function(){
    i++  // only trigger once
});
```



## 结构复用

1. 子组件使用r-html复用数据
2. 子组件使用{#include 复用数据名称}
3. 父组件使用{~加上要复用的结构}传递结构



## 路由

使用的是hash路由

```
 var App = Regular.extend({
            template: `
            <div>
                <h2>主页</h2>
                <div>
                    <a href='#/app/blog'>Go Blog</a>
                </div>
                <div r-view ></div>			//路由组件占位符
            </div>
     `
        })
        var Blog = Regular.extend({
            template: `
            <h2>Blog Page</h2>
            <a href='#/app/blog/chat'>Go chat</a>
            <div r-view ></div>			//路由组件占位符
   `
        })
        var Chat = Regular.extend({
            template: `
                <div><h2>聊天室</h2></div>
   `
        });

        const routes = {
            'app': {		//app为路由名字
                view: App	//app路由对应的组件
            },
            'app.blog': {	//多层的路由组件使用.
                view: Blog
            },
            'app.blog.chat': {
                view: Chat
            }
        }
        var manager = restate()
            //注册路由
            .state(routes).start({ // 启动路由
                view: document.getElementById('app') //顶层容器节点
            });
```

- 使用^符号代表绝对定位



## 路由跳转

1. $state.go( stateName，option，callback )
2. $state.nav( url，option，callback )

callback在路由跳转后被调用

每个路由模块内部都有$state属性，可以用来进行跳转和监听

r-link根据是否以html5模式启动来判断设置的href格式



## 路由守卫

使用manager.on、manager.off、manager.emit来注册、解绑、触发自定义事件

- 第一个参数为触发事件的时机，分别为begin、end、notfound
- 第二个参数则为触发事件的回调函数
  1. begin：在跳转开始时触发，回调函数会获得一个evt参数(option)控制跳转（evt.stop()）
  2. end：在跳转结束后触发，回调函数的参数为koption
  3. notfound：在目标未找到时触发



## 路由的模块缓存机制

1. 默认情况下。到达的节点模块会被缓存，也就是第二次进入后不会再被重新初始化，而是执行enter-mount流程
2. 倘若在leave时销毁组件，则下次进入后会重新初始化。



## 注释

1. <!-- hhh--!>
2. {!hhh!}
