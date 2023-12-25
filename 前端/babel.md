#### 概述：
一个工具集，主要将es6的js代码转换成es5版本的，可以运行在低版本浏览器或其它环境中。
一类文件或库（实质：polyfill.js文件、和@babel/polyfill的npm包。）
在工作中使用ES6编写程序，最后使用Babel将代码转为ES5的代码；转化之后默认是严格模式，通过插件来去除该模式；
主要工作有两部分：
	语法转换
	补齐API
babel默认只转换语法，不转换新的api；

新的api包括：
	一类是Promise、Map、Symbol、Proxy、Iterator等全局对象及其对象自身的方法，例如Object.assign，Promise.resolve；
	一类是新的实例方法，例如数组实例方法[1, 4, -5, 10].find((item) => item < 0)；

#### 安装、配置与转码
一个完整的Babel转码工程包括：
		Babel配置文件：       babel.config.js、或.babelrc、或.babelrc.js、或写在package.json
		Babel相关的npm包
		需要转码的JS文件
简单的使用流程：
		依赖nodejs；
		准备配置文件：babel.config.js、或.babelrc、或.babelrc.js、或写在package.json
		安装3个npm包：
			@babel/cli：    命令行转码工具
			@babel/core：Babel核心npm包。
			@babel/preset-env：提供了ES6转换ES5的语法转换规则；
		命令行执行转码

配置文件
```js
 module.exports = {
    presets: ["@babel/env"],
    plugins: []
  }
```

#### 引入polyfill
通过 Polyfill 的方式在目标环境中添加缺失的特性 。
最常规的做法：使用polyfill为当前环境提供一个垫片；垫片是指垫平不同浏览器之间差异的东西；
polyfill：
	提供了全局的ES6对象；
	通过修改原型链Array.prototype等实现对实例的实现。
使用方式：
	在构建工具入口文件（例如webapck），babel配置文件等方式；
	淘汰：`在html引入 polyfill.js 文件`，
	
