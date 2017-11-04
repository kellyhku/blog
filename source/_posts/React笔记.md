---
title: 第一次使用HEXO
date: 2017-11-01 21:37:23
tags:
---
# 内容反馈

## 移动App
	WebApp
		移动端的浏览器里面运行，不需要下载，只需要有一个url html/css/js
		
		优点：不需要下载，开发成本低
		缺点：体验比不上原生，让用户直接访问比较麻烦
		
	原生(Native)App
		直接运行在操作系统上面，需要下载，java/OC(Swift)
		
		优点：体验好
		缺点：跨平台差，开发成本高，需要下载
		
	混合(hybird)App
		直接运行在操作系统上面，需要下载(比如微信，京东)，原生App里面内嵌一个浏览器来加载我们写好的页面 java/OC(Swift) + 前端
		
		优点：体验好
		缺点：跨平台比较差，开发成本更高，需要下载
		
	微信小程序
		只能用在微信中，大部分使用的是前端技术
		
		优点：不需要安装，用完即走，节约用户的手机存储空间
		缺点：只能在微信中用
		
## RN(React-Native简称)

### RN原理
	1、把我们写的js代码`翻译`成java、OC的代码
	
	2、把翻译好的.java的源代码利用android sdk 编译打包生成可以在操作系统上运行的包 apk/ipa
	
	3、利用android sdk中的adb 将我们打好的包安装运行在真机或是模拟器上
	
	注意:
		1、我们作为前端开发工程师，我们只需要写好js代码
		2、会使用react-native的一系列指令即可
		
### 搭建Android开发环境
	1、安装好jdk，配置好环境变量 使用javac来验证
	
	2、安装python，配置好环境变量，使用python验证
	
	3、解压Android到C盘根目录，配置好环境变量，使用adb验证
	
### 使用react-native-cli脚手架来生成项目
	1、下载 `react-native-cli` `yarn` 两个全局包
	
	2、在桌名（主要是因为没有中文目录），使用`react-native init project_name`，创建项目
	
	3、改源代码里面的 android > gradle > wrapper > gradle-wrapper.properties
		distributionUrl=file\:///C:/Android/gradle-2.14.1-all.zip
		
### 运行在模拟器或是真机
	模拟器
		1、安装夜神，打开USB调试
		
		2、要通过adb连接到我们的夜神模拟器
			adb connect 127.0.0.1:62001
		
		3、切换到项目根目录，使用`react-native run-android`把我们的java代码编译打包，安装运行到模拟器
		
		4、第一次安装的时候，会报错，我们手机没有设置我们node的服务地址
			打开项目 > 菜单键(三个横杠) > Dev Settings > Debug server hostxxx > 你的内网ip:8081
			
		5、关闭掉原先开启的node服务，重新运行`react-native run-android`即可
		
	真机
		1、安装Total Control(手机上没有菜单键)
		
		2、打开手机的USB
		
		3、让我们的电脑和手机处于同一Wifi
		
		4、切换到项目根目录，使用`react-native run-android`把我们的java代码编译打包，安装运行到模拟器
		
		5、第一次安装的时候，会报错，我们手机没有设置我们node的服务地址
			打开项目 > 菜单键(三个横杠) > Dev Settings > Debug server hostxxx > 你的内网ip:8081
			
		6、关闭掉原先开启的node服务，重新运行`react-native run-android`即可

----------------------------

# 今日内容

## React基本知识
	官网:https://reactjs.org/
	中文网址:http://www.css88.com/react/index.html
	
	A JavaScript library for building user interfaces 用于构建用户界面的 JAVASCRIPT 库。
	
	声明式
	基于组件
	学习一次，到处使用
	
	没有指令
	
### 学习资源
	http://www.css88.com/react/docs/hello-world.html
	
	stackoverflow
	
	安装调试工具，方便开发
		React Developer Tools
		
	UI库:
		https://ant.design/index-cn
		
	https://www.awesomes.cn/subject/react#应用-框架
	
### 框架&库
	库
		小而精
		
		针对某一个具体的功能 jquery dom操作
							moment 时间
	
	框架
		vue mui
		大而全
		
		一般是提供一整套解决方案
		
### React四大核心

	虚拟dom
		http://www.infoq.com/cn/articles/react-dom-diff/
		
		Diff算法
	
	JSX
		推荐，如果要想在浏览器中运行，必须通过babel转换
	
	组件
		把相同功能的代码放在一个js、vue中，组件内部做自己的事（发送网路请求、渲染数据），组件内部都有自己独立的作用
	
	单向数据流
		模型(数据，state) ---> 视图
	
-------------------------------

## Webpack+React构建项目
	1、新建必须的文件和文件夹
		src
			main
			App.js
			
		package.json
		
		webpack.develop.config.js
		
	2、在我们页面上面显示`Hello React`
		2.1、安装两个包`react`、`react-dom`
			yarn add react react-dom --save
		
		2.2 在App.js中写好代码
		
		2.3 在main.js中导入App.js，然后使用ReactDom渲染到id=root的div中去
		
	3、在webpack.develop.config.js中写好对应的代码
		(html-webpack-plugin & webpack-dev-server)
		
		3.1 安装 html-webpack-plugin webpack-dev-server webpack
			yarn add html-webpack-plugin webpack-dev-server webpack --dev
			
		3.2 在plugins上配置html-webpack-plugin相关代码
		
		
		3.3 开发阶段，使用webpack-dev-server 打包
			参考:https://webpack.github.io/docs/webpack-dev-server.html
			
			webpack-dev-server --progress --config webpack.develop.config.js --port 3008 --open --hot

	4、在webpack.develop.config.js中配置对`JSX语法的支持`
		需要使用babel
		4.1 安装三个包 babel-core babel-loader babel-preset-react
			webpack必备的包 : `babel-core babel-loader`
		
		4.2 在我们的webpack.develop.config.js的loader添加对.js/.jsx的支持
			具体见代码
			
		4.3 在项目根目录下创建一个babel的配置文件.babelrc在里面配置好预设
			{
			    "presets":["react"]
			}
			
### 构建项目时候的注意事项
	1、每个通过class关键字创建的组件(类组件/有状态组件)，必须要实现一个render方法，否则直接报错
	
	2、在render函数中，要返回jsx语法，return后面必须接东西，否则报错，总之return后面必须接内容(null可以)，否则报错
	
	3、在我们React中所有组件的名称，第一个字母必须大写，否则报错
	
	4、在JSX中的注释要这样写 {/* 被注释的内容 */}
	
	注意:
		大家一定要学会看英文错误
		
### Yarn
	facebook出的，目的是为了取代npm
	
	1、安装全局全局包
		npm i yarn -g
	
	2、使用
		大部分指令和npm差不多，有些还是有差异
		参考:https://yarnpkg.com/zh-Hans/docs/usage
		
		npm i 包名 --save  |  yarn add 包名 --save
		
		npm i 包名 --save-dev | yarn add 包名 --dev

-------------------------------

## React组件

### 概念
	相关功能代码的集合，把功能相似的代码写在同一个文件中，在自己的内部实现业务逻辑，比如发送网络请求，渲染界面
	
### 分类
	状态:数据

#### 无状态组件
	解释:组件内部的数据，只能是父组件传递给我们，我们组件内部，不能拥有自己的数据
	
	代码:
		通过函数来实现的，所以我们的无状态也称之为函数式组件
		
	1、就是一个普通的函数，定义函数的时候，必须导入react这个第三方包
	2、必须返回jsx定义的内容，将来在父组件中呈现出来
	3、我们定义好无状态的子组件之后，就可以在父组件中(App.js)，导入并且使用了
	
	注意点:
		1、在我们的React字符串用`""`，其它类型，传递值&获取值用`{}`
		2、父组件给我们传递过来的值，我们只能用来展示，不能更改
		
	优缺点分析
		缺点:不能拥有自己的数据
		优点:节约内存、代码简单
		
	应用场景:
		纯展示页面的时候用
	
	
#### 有状态组件
	解释:组件内部既可以通过父组件传递数据给我们，又可以自己内部拥有自己的数据
	
	代码:
		是通过es6的class来创建的 
		参考:http://es6.ruanyifeng.com/#docs/class
		
	注意:
		1、有状态组件，必须通过class关键字定义
		2、我们必须在class组件内部实现render方法
		3、父组件给有状态组件传值和父组件给无状态组件传值是一样的
		4、在有状态组件中通过 this.props来接收父组件传递过来的值
		5、有状态组件，自己内部的数据，必须放在state中，这是规定，就像vue中我们组件的数据必须放在data中
		6、如果非要在我们组件的constructor中，拿到父组件的值，这个时候就给我们的constructor给一个形参即可
		7、要更改我们组件内部的state的值，必须通过 setState({
			属性名称:新的值
		}) 改
	
#### 说明
	1、所谓有没有状态是指，组件内部能不能拥有`自己`的数据
	2、每个组件的数据，可以有两个来源，一个是父组件传递给我们，第二个是
	我们自己内部定义

-------------------------------

## React事件机制
	1、React中的事件名称是以驼峰法则命名的
	2、调用事件处理函数的时候，必须写在`{}`
	3、我们在React中事件必须绑定
		绑定的方式如下:
			this.函数名称.bind(this) 【推荐写这种】
			
			()=>{this.函数名称()} 【能看明白】
			
-------------------------------

## React的生命周期
	React组件在内部提供了一些生命周期函数，让我们有机会执行自己的业务逻辑
	
	constructor:
		初始化state
		
	componentWillMount:
		发送网络请求
		
	componentWillUnMount:
		清理资源

-------------------------------

## 其它补充
	在react如果要是用箭头函数，光有react这个预设不够，需要再加一个预设`stage-0`
	
	使用步骤
		1、安装 yarn add babel-preset-stage-0 --dev
		
		2、在.babelrc中配置即可
			{
			    "presets":["react","stage-0"]
			}
	
	静态属性
		defaultProps 给父组件传递过来的值，设置一个默认值，如果没有传递就是用默认值，如果有，就是用父组件传递到过来的值
		
		propTypes 用来校验父组件给我们传递过来值的类型
			参考:https://reactjs.org/docs/typechecking-with-proptypes.html