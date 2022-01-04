

## 相关js库

1. react.js：React核心库。
2. react-dom.js：提供操作DOM的react扩展库。
3. babel.min.js：解析JSX语法代码转为JS代码的库。



## jsx语法规则

1、定义虚拟DOM时，不要写引号。
2、标签中混入Js表达式时要用{}。
3、样式的类名指定不要用class，要用className。
4、内联样式，要用style={{key:value}}的形式去写。
5、只有一个根标签
6、标签必须闭合
7、标签首字母

（1）若小写字母开头，则将改标签转为html中同名元素，若html中无该标签对应的同名元素，则报错。
（2）若大写字母开头，react就去渲染对应的组件，若组件没有定义，则报错。

8、加注释：

```
{/*注释内容*/}
```





 Babel 会把 每一个JSX 转译成一个名为 `React.createElement()` 函数调用。 

```
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```

```
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```



## 组件

组件自定义方法中的this为underfined

- 原因：react将函数传递给jsx,且类中的方法默认开启了局部的严格模式，严格模式下this为undefined 

- 解决方法：
  1. 通过bind绑定函数的this
  2. 使用箭头函数

组件传递标签属性可以使用三点运算符解构对象



函数组件跟类组件的区别：

- 函数组件和类组件当然是有区别的，而且函数组件的性能比类组件的性能要高，因为类组件使用的时候要实例化，而函数组件直接执行函数取返回结果即可。
- 函数组件没有this，生命周期和状态



## state

作用：存放当前组件的状态

状态不能直接更改，需要调用setState方法去修改

添加/修改状态：this.setState({修改的属性名：修改后的值})

setState引起react后续更新状态的动作是异步的

setstate的第一种格式，第一个参数是一个对象，第二个参数是一个回调函数，这个回调函数是在setstate执行完并页面渲染了之后再执行 。

setstate的第二种格式，接收一个回调函数，这个回调函数有两个参数，一个是接收前一个状态值作为第一个参数，并将更新后的值作为第二个参数。

- 修改状态的动作为合并动作，也就是将修改的属性合并到所有的状态
- React 可能会把多个 `setState()` 调用合并成一个调用。 



## props

作用：接收组件传来的属性

组件内部不能修改props的值



对props中的属性值进行限制

- ```
  Person.propTypes = {
   name: React.PropTypes.string.isRequired,
   age: React.PropTypes.number
  }
  ```

给props设置默认属性值

- ```
  Person.defaultProps = {
    age: 18,
    sex:'男'
  }
  ```




构造函数接收的props用于给super提供参数，只有super函数有props参数，在构造函数中才可以使用this.props的数据

类的所有方法都定义在类的`prototype`属性上面。||类是建立在原型之上



## ref

作用：组件内的标签可以通过定义ref属性来标识自己

如何通过refs来访问DOM节点：

1. 字符串形式的ref

   ```
   <input ref="input1"/>
   ```

2. 回调形式的ref

   ```
   <input ref={(c)=>{this.input1 = c}}
   ```

   如果ref回调函数是以内联函数的方式定义的，在更新过程中(render)它会被执行两次，因为 ref的回调函数会在ref改变时触发 ，第一次传入参数null，然后第二次会传入参数DOM元素。这是因为在每次渲染时会创建一个新的函数实例，所以React清空旧的ref并且设置一个新的。通过将ref的回调函数定义成class的绑定函数的方式可以避免上述问题。

这样用的好处在于，react可以更优雅的完成对组件销毁时的变量回收，你只要这么用，react在销毁组件时，this.test 很方便的就可以被清理变为null。

另一好处：ref是一个回调函数，使得我们能在这个函数中做更多的事情，比如说，我们可以借助这种函数的机制，让父组件直接获取子组件的Dom。而如果你让ref是一个字符串，实现这个功能是不可能的，代码如下：

```
function CustomTextInput(props) {
  return (
    <div>
      <input ref={props.inputRef} />
    </div>
  );
}

class Parent extends React.Component {
  render() {
    return (
      <CustomTextInput
        inputRef={el => this.inputElement = el}
      />
    );
  }
}	
```



1. createRef创建ref容器·

   ```
   myRef = React.createRef() 
   <input ref={this.myRef}/>
   ```

   

## render

触发render函数的时期：

1. 实例化的过程中
2. 修改组件的状态后



## 生命周期

1. 初始化阶段：由ReactDOM.render()触发	--初次渲染
   - constructor()
   - componentWillMount()      //即将在18版本废弃
   - getDerivedStateFromProps()
     - 此钩子前面必须要用static修饰
     - 此钩子必须要有返回值，且返回值必须为状态对象或者NULL
     - 此钩子的返回值如果是状态对象，那返回的状态只受到props的影响
   - render()
   - componentDidMount()
2. 更新阶段：由组件内部this.SetState()或父组件重新触发render
   - shouldComponentUpdate()
   - componentWillUpdate()      //即将在18版本废弃
   - render()
   - getSnapshotBeforeUpdate()
     -  这个方法能够使得组件可以在更改之前从 更改前的DOM中 捕获一些信息 
     - 必须返回一个值或者null
   - componentDidUpdate(preProp,preState,getSnapshotBeforeUpdate的返回值)
3. 卸载组件:由ReactDOM.unmountComponentAtNode()触发
   - componentWillUnmount()



## key

作用：key是虚拟DOM对象的标识，在更新显示时key起着极其重要的作用。当状态中的数据发生改变时，react会根据新数据生成新的虚拟DOM，随后React进行新的虚拟DOM与旧的虚拟DOM的diff比较。

- diff比较
  - 旧虚拟DOM中找到了与新的虚拟DOM相同的key
    1. 若虚拟DOM中的内容没有改变，直接使用之前的真实DOM
    2. 若虚拟DOM中的内容改变了，则生成新的虚拟DOM，随后替换掉页面之前是真实DOM
  - 旧虚拟DOM中未找到与新的虚拟DOM相同的key
    1. 根据数据创建新的真实DOM，随后渲染到页面



## 使用脚手架创建项目

1. 全局安装脚手架：npm i create-react-app -g
2. 创建项目：create-react-app name

用react脚手架创建的项目结构：

```
	public ---- 静态资源文件夹
		favicon.icon ------ 网站页签图标
		index.html -------- 主页面
		logo192.png ------- logo图
		logo512.png ------- logo图
		manifest.json ----- 应用加壳的配置文件
		robots.txt -------- 爬虫协议文件
	src ---- 源码文件夹
		App.css -------- App组件的样式
		App.js --------- App组件
		App.test.js ---- 用于给App做测试
		index.css ------ 样式
		index.js ------- 入口文件
		logo.svg ------- logo图
		reportWebVitals.js
			--- 页面性能分析文件(需要web-vitals库的支持)
		setupTests.js
			---- 组件单元测试的文件(需要jest-dom库的支持)
```



## react脚手架配置代理

1. 在package.json中追加如下配置

   ```json
   "proxy":"http://localhost:5000"
   ```

   说明：

   1. 优点：配置简单，前端请求资源时可以不加任何前缀。
   2. 缺点：不能配置多个代理。
   3. 工作方式：上述方式配置代理，当请求了3000不存在的资源时，那么该请求会转发给5000 （优先匹配前端资源）

2. 第一步：创建代理配置文件

```
在src下创建配置文件：src/setupProxy.js
```

第二步：编写setupProxy.js配置具体代理规则：

```js
const proxy = require('http-proxy-middleware')

module.exports = function(app) {
  app.use(
    proxy('/api1', {  //api1是需要转发的请求(所有带有/api1前缀的请求都会转发给5000)
      target: 'http://localhost:5000', //配置转发目标地址(能返回数据的服务器地址)
      changeOrigin: true, //控制服务器接收到的请求头中host字段的值
      /*
      	changeOrigin设置为true时，服务器收到的请求头中的host为：localhost:5000
      	changeOrigin设置为false时，服务器收到的请求头中的host为：localhost:3000
      	changeOrigin默认值为false，但我们一般将changeOrigin值设为true
      */
      pathRewrite: {'^/api1': ''} //去除请求前缀，保证交给后台服务器的是正常请求地址(必须配置)
    }),
    proxy('/api2', { 
      target: 'http://localhost:5001',
      changeOrigin: true,
      pathRewrite: {'^/api2': ''}
    })
  )
}
```

说明：

1. 优点：可以配置多个代理，可以灵活的控制请求是否走代理。
2. 缺点：配置繁琐，前端请求资源时必须加前缀。



## 路由

1. Link:相当于a标签
2. Redirect：重定向，必须放在Switch里最后一行，当点击路由链接或者进行路由跳转时，若匹配不到路由组件，则重定向到to指定的地址
3. Navlink：主要用于给导航点击时添加active类,也可以自己定义点击后的类名，为activeClassName
4. Switch标签：

- 若Switch内的route的路径相同时，只匹配第一个，避免重复匹配
- 若没有用Switch包裹路由，则相同路径的route都会被匹配



#### 解决多级路径刷新页面样式丢失问题

1. 引入样式时写/
2. 引入样式时写%PUBLIC_URL%
3. 使用HashRouter



路由精准匹配：往路由组件添加exact属性，值为true

路由的匹配是按照路由注册的顺序进行匹配



#### 路由参数

**params参数**

在this.props.match.params获取路由参数

```
<Link to={`/home/message/detail/${obj.id}`}>${obj.name}</Link>
```

**search参数**

在this.props.location.searach获取路由参数，然后通过querystring.parse将路由参数转换为对象

```
<Link to={`/home/message/detail?id=${obj.id}`}>${obj.name}</Link>
```

**state参数**

在this.props.location.state获取路由参数,在请求某个路由时路由参数在URL不可见

```
<Link to={{pathname:'/home/message/detail',state:{id:456,name:'lisi'}}}>${obj.name}</Link>
```

HashRouter刷新后会导致路由state参数的丢失，BrowserRouter刷新后不会丢失state参数



#### 路由跳转模式

1. push模式

   将路由往路由栈中添加

2. replace模式

   将路由栈的栈顶路由替换



#### history对象

他的API可操作路由跳转、前进、后退

- this.props.history.push()
- this.props.history.replace()
- this.props.history.goBack()
- this.props.history.goForward()
- this.props.history.go()



**给普通组件添加路由组件API**

```
class Header extends Component{}
export default withRouter(Header)
```



## antd

1. 下载antd

   ```
   npm install --save antd
   ```

2. 样式的按需导入

   - ```
     npm install react-app-rewired customize-cra
     ```

   - 修改package.json

     ```
     "scripts": {
        "start": "react-app-rewired start",
        "build": "react-app-rewired build",
        "test": "react-app-rewired test",
     }
     ```

   - ```
     npm install babel-plugin-import
     ```

   - 在根目录创建一个config-overrides.js用于修改配置

     ```
     const { override, fixBabelImports } = require('customize-cra');
     
     module.exports = override(
        fixBabelImports('import', {
          libraryName: 'antd',
          libraryDirectory: 'es',
          style: 'css',
        }),
     );
     ```

3. 自定义主题颜色

   先引入less和less-loader

   ```
   npm install less less-loader
   ```

   再修改config.overrides.js

   ```
   const { override, fixBabelImports, addLessLoader } = require('customize-cra');
   
   module.exports = override(
     fixBabelImports('import', {
       libraryName: 'antd',
       libraryDirectory: 'es',
      style: 'css',
      style: true,
     }),
    addLessLoader({
    	lessOptions:{
           javascriptEnabled: true,
          	modifyVars: { '@primary-color': '#1DA57A' },
    	}
    }),
   );
   ```

   

## redux

- store对象

  ```
  //引入createStore，专门用于创建redux中最为核心的store对象
  import {createStore} from 'redux'
  //引入为Count组件服务的reducer
  import countReducer from './count_reducer'
  //暴露store
  export default createStore(countReducer)
  ```

- reducer对象

  1. 该对象本质上为函数，reducer函数会接收到两个参数，为之前的状态和动作对象
  2. reducer作用：初始化状态和加工状态
  3. reducer被第一次调用是由store自动触发的，传递的preState是underfined，传递的action是{type:'@@REDUX/INIT_a.2.b.4'}
  
  

获取状态属性

store.getState()

操作状态属性值

store.dispatch(action)//action必须拥有type属性，action为对象时是同步，为函数时为异步

检测状态属性值的变化

store.subscribe(()=>{})



## react-redux

1. 所有的UI组件都应该包裹一个容器组件（count）
2. 容器组件是真正和react-redux交互的，在容器组件可以使用react-redux的API
3. UI组件中不能使用任意react-redux的API
4. 容器组件会传给UI组件的内容为：redux的状态和操作状态的方法
5. 容器给UI组件传递状态和操作状态的方法都是通过props传递



## 路由懒加载

lazyload和suspence

```
import React,{Component,lazy,suspence} from 'react'
//1.通过React的lazy函数配合import()函数动态加载路由组件 ===> 路由组件代码会被分开打包
const Login = lazy(()=>import('@/pages/Login'))
	
//2.通过<Suspense>指定在加载得到路由打包文件前显示一个自定义loading界面
<Suspense fallback={<h1>loading.....</h1>}>
    <Switch>
        <Route path="/xxx" component={Xxxx}/>
        <Redirect to="/login"/>
    </Switch>
</Suspense>
```



## Hooks

作用：可以在函数组件中使用state以及其他react属性

- **state Hooks**

  ```
  (1). State Hook让函数组件也可以有state状态, 并进行状态数据的读写操作
  (2). 语法: const [xxx, setXxx] = React.useState(initValue)  
  (3). useState()说明:
          参数: 第一次初始化指定的值在内部作缓存
          返回值: 包含2个元素的数组, 第1个为内部当前状态值, 第2个为更新状态值的函数
  (4). setXxx()2种写法:
          setXxx(newValue): 参数为非函数值, 直接指定新的状态值, 内部用其覆盖原来的状态值
          setXxx(value => newValue): 参数为函数, 接收原本的状态值, 返回新的状态值, 内部用其覆盖原来的状态值
  ```

- **effect Hooks**

  ```
  (1). Effect Hook 可以让你在函数组件中执行副作用操作(用于模拟类组件中的生命周期钩子)
  (2). React中的副作用操作:
          发ajax请求数据获取
          设置订阅 / 启动定时器
          手动更改真实DOM
  (3). 语法和说明: 
          useEffect(() => { 
            // 在此可以执行任何带副作用操作
            return () => { // 在组件卸载前执行
              // 在此做一些收尾工作, 比如清除定时器/取消订阅等
            }
          }, [stateValue]) // 如果指定的是[], 回调函数只会在第一次render()后执行
          
      第二个参数为可选项，不传此参数时表示在组件挂载或更新时执行此hook.可传入数组，数组里可以为空，表示不依赖任何状态的变化，即只在组件即将挂载时执行，后续任何状态发生了变化，都不调用此hook。数组里也可以定义一或多个状态，表示每次该状态变化时，都会执行此hook。
      
  (4). 可以把 useEffect Hook 看做如下三个函数的组合
          componentDidMount()
          componentDidUpdate()
      	componentWillUnmount() 
  ```

- **ref Hooks**

  ```
  (1). Ref Hook可以在函数组件中存储/查找组件内的标签或任意其它数据
  (2). 语法: const refContainer = useRef()
  (3). 作用:保存标签对象,功能与React.createRef()一样
  ```



## fragment

**使用**

	<Fragment><Fragment>
	<></>

**作用**

> 可以不用必须有一个真实的DOM根标签了



## 插槽

父组件在子组件中间夹结构

```
          <ChildCom>
              <h1 data-position="header">这是放置到头部的内容</h1>
              <h1 data-position="main">这是放置到主要的内容</h1>
              <h1 data-position="footer">这是放置到尾部的内容</h1>
          </ChildCom>
```

子组件通过this.props.children获取插槽的内容

通过item.props['data-position']对比插槽的标记从而获取具体插槽的某一个元素