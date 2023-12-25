创建vue应用、vue应用实例：通过createApp工厂函数来创建实例，createApp中是根实例；在mainjs文件中
```js
import { createApp } from 'vue'

const app = createApp({
  /* 根组件选项 */
})

import App from './App.vue'     //单文件组件需从另一个文件中导入根组件

```
通过createApp方法可以返回一个提供应用上下文的应用实例。不同实例注册的组件无法在不同的实例下使用。
	两个vue应用各自注册的组件不能相互使用；






使用路由模式：
	 `history` 参数而并非mode；







**安装**：
	$ npm install vue     ；构建大型应用时用npm安装；npm可以和webpack、  Browserify 模块打包器配合使用；
	vue所需的环境：npm+node；
**命令行工具 (CLI)**

	无需构建步骤，渐进式增强静态的 HTML
	在任何页面中作为 Web Components 嵌入
	单页应用 (SPA)
	全栈 / 服务端渲染 (SSR)
	Jamstack / 静态站点生成 (SSG)
	开发桌面端、移动端、WebGL，甚至是命令行终端中的界面


指令：v-
v-on：事件监听器，通过它调用方法


#### vue-cli
脚手架工具。简化了基于webpack创建工程化项目的过程。
安装
	安装nodejs
	使用命令行安装：1、npm install –g @vue/cli    2、查看版本vue --version//全局安装，只需安装一次后续直接使用
	创建项目：vue create  XXX
	运行项目npm run dev
	查看webpack配置分析，开发与生产环境
	打包上线：npm run build 生产环境
	

vue3

**单文件组件**（即.vue文件）  ————vue的标志性功能，类似 HTML 格式的文件
将逻辑js、模板html、样式css封装在一个文件里；

#### API 风格
包含**选项式 API** 和**组合式 API**，选项式 API 是在组合式 API 的基础上实现
**选项式 API** ：用包含`data`、`methods` 和 `mounted`等选项的对象来描述逻辑；定义的属性都会暴露在函数内部的 `this` 上，它会指向当前的组件实例。

**组合式 API**：导入的 API 函数来描述组件逻辑
- 与 [`<script setup>`](https://cn.vuejs.org/api/sfc-script-setup.html) 搭配使用





