概述
	js框架、渐进式框架、核心库只关注视图层。Vue.js 核心是一个可采用简洁的模板语法来声明式地将数据渲染进 DOM 的系统；
	组件系统：可预定义的vue实例；可用小型、独立、可复用的组件构建大型应用；可抽象成一个组件树；
	过渡效果：提供一个强大的过渡效果系统，如在操作元素时；
	





vue2


####  介绍
Vue.js 的核心是一个允许采用简洁的模板语法来声明式地将数据渲染进 DOM 的系统：
 Vue 里，一个组件本质上是一个拥有预定义选项的一个 Vue 实例



#### vue实例
创建应用、应用实例。main.js文件中；
```js
 const app = new Vue({
		el：挂载点，可以是元素，也可以是 CSS 选择器，支持原生 JS 写法
		data：代理数据
		methods：定义方法
		....
		选项对象1,
		选项对象2,
        ...
    })

或
new Vue({
  router,
  store,
  render: h => h(App)
}).$mount('#app')

mount 方法执行后返回的是【根组件】实例，并不是【应用实例】
```

一个 Vue 应用：【new Vue 创建的根 Vue 实例】(只能有一个) +【组件树】(所有vue组件都是vue实例）组成；
	所有Vue实例是共享一个Vue构造函数对象的，包括全局指令/全局组件，无法做到相互隔离。【两个vue应用可以共享一个组件】，其他的单文件组件创建的 Vue实例都会成为它的子实例。
**实例化组件**
	模板中的< MyComponent ...></MyComponent>
	render 函数中使用 createElement 创建；






响应式：
	Vue 实例被创建时，`data` 对象中的所有的 属性 加入到 Vue 的**响应式系统**中，属性改变——视图会响应更新值。只有在实例创建时就已经存在于data中的属性才是响应式的。（数据改变时，视图会从新渲染）
	唯一的例外是使用 Object.freeze(data)，这会阻止修改现有的属性，也意味着响应系统无法再追踪变化。
vue实例的一些属性与方法
	都具有前缀前缀 $，（与用户定义区分）
	vm.$watch，观察变量的前后变化与值。        
				vm.$watch('变量名', function (newValue, oldValue) {   // 这个回调将在 `vm.a` 改变后调用})

生命周期
vue实例创建的初始化开发过程，过程中会运行一些叫做**生命周期钩子**的函数，这给了用户在不同阶段添加自己的代码的机会
	如，数据监听、编译模板、将实例挂载到 DOM 并在数据变化时更新 DOM 等
需要写在new Vue（）对象内，以属性函数的方式进行声明，生命周期函数内不能使用箭头函数，因为需要使用this；
	beforeCreate：function（）{}；在vue应用运行的每个阶段自动调用；在页面被创建之前调用；
	creat（）
	beforemount（）
	mounted（）
	beforeupdate（）
	updated（）



#### 模板语法
- vue.js 使用了基于 HTML 的模板语法，允许开发者声明式地将 DOM 绑定至底层 Vue 实例的数据。
- 所有 Vue.js 的模板都是合法的 HTML，所以能被遵循规范的浏览器和 HTML 解析器解析。
- 在底层的实现上，Vue 将模板编译成虚拟 DOM 渲染函数。结合响应系统，Vue 能够智能地计算出最少需要重新渲染多少组件，并把 DOM 操作次数减到最少。
- 如果熟悉虚拟 DOM 并且偏爱 JavaScript 的原始力量，你也可以不用模板，直接写渲染 (render) 函数，使用可选的 JSX 语法。

插值
	文本
		数据绑定：使用“Mustache”语法 (双大括号)，将数据解释为普通文本而非html。`<span>Message: {{ msg }}</span>`
			使用 v-once 指令，你也能执行一次性地插值，当数据改变时，插值处的内容不会更新。但请留心这会影响到该节点上的其它数据绑定。
	原始html
		标签内使用 v-html 指令。
		只对可信内容使用 HTML 插值，绝不要对用户提供的内容使用插值。否则易导致 XSS 攻击
	标签的属性
		使用vue.js为html标签动态绑定html标签的属性， 使用 v-bind 指令：`<div v-bind:属性名="变量"></div>`，该变量可从data中获取。
	js表达式
		 对于所有的绑定都支持
指令
	带有v- 前缀的特殊属性。单个 JavaScript 表达式，当值改变时，响应式的作用于dom。
	参数 
		指令可接受参数，指令名称后用冒号表示，如，v-bind；
		动态参数，v-bind:[attributeName]="url"；
			attributeName，用js表达式动态求值；预期是一个字符串，非字符串会警告；表达式有语法约束：如空格和引号。
	指令的修饰符
		以半角句号 . 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定。
		如，嵌套的click事件中，可通过click.stop=‘function（）’，.stop   实现只在内层中处理点击事件，外层的事件不响应处理。
缩写
	一般情况，v- 前缀作为一种视觉提示，用来识别模板中 Vue 特定的 attribute。
	在单页面应用程序中，频繁用到，则可简写
		v-bind       ：
		v-on: click=         @click=



#### 计算属性和侦听器
计算属性
	在数据绑定中，可使用表达式进行计算。但当表达式比较复杂时应该使用计算属性：将复杂的表达式写成一个函数形式（计算属性的getter函数）放入属性computed属性中。
	计算属性对比方法是基于它们的响应式依赖进行缓存的，只在相关响应式依赖发生改变时它们才会重新求值，指依赖的变量未发生改变。
	计算属性默认只有 getter，不过在需要时你也可以提供一个 setter
计算属性对比侦听属性
	更通用的方式来观察和响应 Vue 实例上的数据变动
	当你有一些数据需要随着其它数据变动而变动时，最好使用计算属性而不是命令式的 watch 回调。
侦听属性
	watch
			当需要在数据变化时执行异步或开销较大的操作时，这个方式是最有用的。
			如，使用 watch 选项允许我们执行异步操作 (访问一个 API)，限制我们执行该操作的频率，并在我们得到最终结果前，设置中间状态。这些都是计算属性无法做到的。
	使用命令式的 vm.$watch API。



#### Class 与 Style 绑定
绑定 HTML Class
	v-bind:class 
		- 赋一个对象，实现动态切换class，如`<div v-bind:class="{ active: isActive }"></div>`；可与普通的 class共存，在已有普通class名基础上再添加v-bind的动态class名。
		- 可赋数组；要动态切换class，可在数组内部使用三元运算。
		- 用在组件上：当在一个自定义组件上使用 class property 时，这些 class 将被添加到该组件的根元素上面。这个元素上已经存在的 class 不会被覆盖。
绑定内联样式
	v-bind:style
		赋对象，可直接绑定一个样式对象在data中，
		赋数组，可以将多个样式对象应用到同一个元素上。
	自动添加前缀
		当 v-bind:style 使用需要添加浏览器引擎前缀的 CSS property 时，如 transform，Vue.js 会自动侦测并添加相应的前缀。
	多重值
		可以为 style 绑定中的 property 提供一个包含多个值的数组，常用于提供多个带前缀的值，且只会渲染数组中最后一个被浏览器支持的值。





#### 条件渲染
v-if
	v-if 指令用于条件性地渲染一块内容，为true时。这块内容只会在指令的表达式返回 truthy 值的时候被渲染。
	v-else，表示 v-if 的“else 块”；
	v-else-if， v-if 的“else-if 块”，可以连续使用，类似于 v-else，v-else-if 也必须紧跟在带 v-if 或者 v-else-if 的元素之后。——2.1.0 新增
	在 `<template> `元素上使用 v-if 条件渲染分组
v-show
	值为true时渲染。
	v-show 不支持 `<template>` 元素，也不支持 v-else。
if与show指令对比
	v-if：
		真正的条件渲染，确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。
		条件为假，什么也不做。
		更高的切换开销；
		适用条件很少改变情况；
	v-show：
		管初始条件是什么，元素总是会被渲染。并且只是简单地基于 CSS 进行切换。
		更高的初始渲染开销
		适用频繁地切换。
用 key 管理可复用的元素
	Vue 会尽可能高效地渲染元素，通常会复用已有元素而不是从头开始渲染。当不想要这样复用时，可在复用元素上添加key属性并各自赋上唯一值。
不推荐同时使用 v-if 和 v-for。




#### 列表渲染

遍历对象时，会按 Object.keys() 的结果遍历
 v-for ——用数组渲染列表
	 使用 item in items 形式
	 可以访问所有父作用域的 property。
	 支持一个可选的第二个参数，即当前项的索引。v-for="(item, index) in items"
	 也可以用 of 替代 in 作为分隔符，更接近 JavaScript 迭代器的语法
 v-for ——用对象渲染列表
	 v-for="value in object"   ，或键值 v-for="(value, name) in object" ，或索引 v-for="(value, name, index) in object"

维护状态
	渲染时，若数据项的顺序被改变
		Vue 将不会移动 DOM 元素来匹配数据项的顺序，而是就地更新每个元素，并且确保它们在每个索引位置正确渲染。
			只适用于不依赖子组件状态或临时 DOM 状态 (例如：表单输入值) 的列表渲染输出。
		为了给 Vue 一个提示，以便它能跟踪每个节点的身份，从而重用和重新排序现有元素，你需要为每项提供一个唯一 `key` attribute。
		建议尽可能在使用 `v-for` 时提供 `key` attribute，除非遍历输出的 DOM 内容非常简单，或者是刻意依赖默认行为以获取性能上的提升。它是 Vue 识别节点的一个通用机制。
		不要使用对象或数组之类的非基本类型值作为 `v-for` 的 `key`。请用字符串或数值类型的值。

  数组更新检测
	  数组的变更方法也会触发视图更新。push, pop, shift,等等
	  替换数组，当使用非变更方法时，可以用新数组替换旧数组。
	  由于 JavaScript 的限制，Vue 不能检测数组和对象的变化。深入响应式原理中有相关的讨论。

显示过滤/排序后的结果
	想要显示一个数组经过过滤或排序后的版本，而不实际变更或重置原始数据。在这种情况下，可以创建一个计算属性，来返回过滤或排序后的数组。

在`<template>`上使用 v-for
	可以利用带有 v-for 的 `<template> `来循环渲染一段包含多个元素的内容。
在组件上使用 v-for
	在自定义组件上，你可以像在任何普通元素上一样使用 v-for。
	2.2.0+ 的版本里，当在组件上使用 v-for 时，key 现在是必须的。
	任何数据都不会被自动传递到组件里，因为组件有自己独立的作用域。为了把迭代数据传递到组件里，我们要使用 prop；
	不自动将 item 注入到组件里的原因是，这会使得组件与 v-for 的运作紧密耦合。明确组件数据的来源能够使组件在其他场合重复使用。



#### 事件处理

用 v-on 指令监听 DOM 事件，并触发事件处理程序。   v-on:click="counter += 1" ；    v-on:click="greet"
	可在v-on写表达式
	一般使用方法调用
		实例method属性中的方法调用；
		内联处理器中的方法；
			在内联 JavaScript 语句中调用方法：v-on:click="say('what')"
			事件作参数：在内联语句处理器中访问原始的 DOM 事件，用特殊变量 $event 把它传入方法，v-on:click="greet('abc', $event)"
事件修饰符
	因为经常在事件处理程序中调用 event.preventDefault() 或 event.stopPropagation()；
	但更好的方法：只有纯粹的数据逻辑，而不是去处理 DOM 事件细节。
	所以，Vue.js 为 v-on 提供了事件修饰符，修饰符是由点开头的指令后缀来表示的。
			v-on:click.stop="doThis"
	使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。因此，用 v-on:click.prevent.self 会阻止所有的点击，而 v-on:click.self.prevent 只会阻止对元素自身的点击。
	.stop
	.prevent
	.capture
	.self
	.once
	.passive

按键修饰符
	Vue 允许为 v-on 在监听键盘事件时添加按键修饰符
系统修饰键
	可以用如下修饰符来实现仅在按下相应按键时才触发鼠标或键盘事件的监听器。
		.ctrl
		.alt
		.shift
		.meta
.exact 修饰符
	允许你控制由精确的系统修饰符组合触发的事件。

在 HTML 中监听事件原因
	使用 v-on 有几个好处：
		扫一眼 HTML 模板便能轻松定位在 JavaScript 代码里对应的方法。
		因为你无须在 JavaScript 里手动绑定事件，你的 ViewModel 代码可以是非常纯粹的逻辑，和 DOM 完全解耦，更易于测试。
		当一个 ViewModel 被销毁时，所有的事件处理器都会自动被删除。你无须担心如何清理它们。

Vue.use
	用法：
		安装 Vue.js 插件。
			如果插件是一个对象，必须提供 install 方法。
			如果插件是一个函数，它会被作为 install 方法。install 方法调用时，会将 Vue 作为参数传入。
		该方法需要在调用 new Vue() 之前被调用。
		针对Vue编写的插件用Vue.use导入；
Vue.prototype
	如果需要设置全局变量或全局方法，并且不想污染全局作用域；以通过在原型上定义它们使其在每个Vue 的实例中可用。
	不是针对Vue编写的插件用Vue.prototype导入；


#### 表单输入绑定
概述
	用 v-model 指令在表单` <input>、<textarea> 及 <select> `元素上创建双向数据绑定。即v-model="str"，多处同时使用str的值且同步更新。
	本质上不过是语法糖。它负责监听用户的输入事件以更新数据，并对一些极端场景进行一些特殊处理。
基本用法
	v-model 会忽略所有表单元素的的初始值而总是将 Vue 实例的数据作为数据来源。应该通过 JavaScript 在组件的 data 选项中声明初始值。
	v-model 在内部为不同的输入元素使用不同的 property 并抛出不同的事件：
		text 和 textarea 元素使用 value property 和 input 事件；
		checkbox 和 radio 使用 checked property 和 change 事件；
		select 字段将 value 作为 prop 并将 change 作为事件。
	在文本区域插值 (`<textarea>{{text}}</textarea>`) 并不会生效，应用 v-model 来代替。
	如果 v-model 表达式的初始值未能匹配任何选项，`<select>` 元素将被渲染为“未选中”状态。在 iOS 中，这会使用户无法选择第一个选项。因为这样的情况下，iOS 不会触发 change 事件。因此，更推荐像上面这样提供一个值为空的禁用选项。
	值绑定
		对于单选按钮，复选框及选择框的选项，v-model 绑定的值通常是静态字符串 (对于复选框也可以是布尔值)
		想把值绑定到 Vue 实例的一个动态 property 上，这时可以用 v-bind 实现，并且这个 property 的值可以不是字符串。

修饰符
	.lazy          `<input v-model.lazy="msg">`
		在默认情况下，v-model 在每次 input 事件触发后将输入框的值与数据进行同步 (除了上述输入法组合文字时)。你可以添加 lazy 修饰符，从而转为在 change 事件_之后_进行同步
	.number    `<input v-model.number="age" type="number">`
		给 v-model 添加 number 修饰符, 自动将用户的输入值转为数值类型。
	.trim
		自动过滤用户输入的首尾空白字符

在组件上使用 v-model
	Vue 的组件系统允许你创建具有完全自定义行为且可复用的输入组件。这些输入组件甚至可以和 v-model 一起使用.

v-bind：通过绑定可实现组件间值的传递，但只在初始化的时候数据绑定到视图上，后续视图变化不会影响数据；
v-model：也实现值的传递，但也实现页面数据的实时变化，一方变化，另一方也同时变化。




### 组件

#### 组件基础
概述
	const app=Vue.creatApp({});    //创建vue应用
	app.component('组件名称',{data,template等等})   //定义一个全局组件，名称命名：驼峰或短横线
组件的创建
	vue使用Vue.component函数去创建组件。
			Vue.component('my-component-name', {              参数1：组件名称，参数2：数据和模板内容，
					  // ... options ...
			})
构成
	组件是可复用的 Vue 实例，一个组件就是一个新的实例。可在任何 vue根实例模板中应用；
	本质：所有的Vue组件都是Vue的子类实例；Vue组件构造类是继承自Vue类；
	开发中可将重复的功能封装为组件，组件可任意次数复用。
	与 `new Vue` 接收相同的选项，如 `data`、`computed`、`watch`、`methods` 以及生命周期钩子等，例外：`el` 这样根实例。
	data：一个组件的 data 选项必须是一个函数，每个实例可以维护一份被返回对象的独立的拷贝。
	Props：
		可以在组件上注册的一些自定义属性；
		不限数量，不限任何值。
		单向数据流，只能从父到子组件。
		该值由父组件拥有，只能以只读的形式传递给子组件，不可修改其值。
			子组件的方法：复制到新变量上；或通过计算属性处理props的值
		props接受的类型：
			字符串，数字，布尔值，数组，对象(有v-bind="对象名")，日期，函数，Symbol，和自定义构造函数(可通过instanceof验证)。
			类型不匹配则警告，props: {firstName: String},
		prop的验证：
			可在prop内部用validator验证函数；那些 prop 会在一个组件实例创建之前进行验证，所以实例的 property (如 data、computed 等) 在 default 或 validator 函数中是不可用的。
		props的默认值：
			可在子组件的props中设置default属性。
		属性集成
			非 Prop 的 Attribute
				指未被prop 定义的传向子组件的属性，如在父组件的子组件标签上的元素属性，会被自动添加到子组件的根元素节点上，作为元素属性。
		替换/合并已有的 Attribute
			当子组件内部的元素属性和父组件在子组件标签上定义的元素属重合时，元素的一般属性会被替换，但class和style属性会被合并。
		禁用 Attribute 继承
			当不需要子组件的根元素继承父组件在子组件标签上的非prop属性时，可在注册组件时加上选项inheritAttrs: false；
			应用场景
				需要将该元素属性运用到非根元素上时，如根元素的子元素。可用$attrs访问这些非prop的属性。




#### 组件注册
组件的两种注册类型
	**全局注册**：
		Vue.component(' ',{  })方法；全局注册的组件可以用在其被注册之后的任何 (通过 new Vue) 新创建的 Vue 根实例，也包括其组件树中的所有子组件的模板中。全局注册的行为必须在根 Vue 实例 (通过 new Vue) 创建之前发生。
	**局部注册**
		1、全局注册对于在webpack构建系统中的构建结果仍会包含一个不再使用的全局组件，会造成用户下载js的多余和浪费。可使用局部注册。
		2、通过在创建vue对象时（即vue函数初始化时），在vue函数的一个对象参数的内部声明components属性内部进行注册组件，并以一个键值对的形式表示一个组件，值内包含template，data等等，
			如      components: {
						'component-a': {template:...,methods }, 
						'component-b': ComponentB
						}
		3、局部注册的组件在其子组件中不可用。
组件名
	命名方式
		 短横线法kebab-case：都小写用短横线；在dom中直接使用组件时（非字符串和非单文件组件）仅该方法有效。
		 大驼峰PascalCase，每个首字母大写

模块系统
	在模块系统中局部注册（如webpack）
		通过import从模块目录中引入组件、在vue对象中内部components属性中 进行组件的局部注册。
	基础组件的自动化全局注册
		对通用的频繁用到的基础组件，为了避免导入时的大长串问题，且当使用了webpack系统时，可使用 require.context 只全局注册这些非常通用的基础组件。





#### 动态组件
概述
	动态组件：动态切换组件；当需要频繁地切换组件时。（如多标签页面）
	用法
		需切换的组件comA，comB等时，在需要切换组件的位置处的外部用`<component>`元素包裹，并用v-bind动态绑定 is属性的值为data中的comA，comB值；
keep-alive
	为了在组件切换过程中保持前组件的状态，避免反复重新渲染；
	注意这个 < keep-alive> 要求被切换到的组件都有自己的名字，不论是通过组件的 name 选项还是局部/全局注册。
	用法
		在component元素外部直接包裹< keep-alive>< /keep-alive>标签；

#### 异步组件
当有部分组件只在需要时才从服务器中加载时；用工厂函数的方式定义组件，工厂函数会异步解析该组件的定义；当需要渲染该组件时，会触发工厂函数，并将结果缓存以供之后使用；
```js
Vue.component('async-example', function (resolve, reject) {  
	setTimeout(function () {  
	// 向 `resolve` 回调传递组件定义  
		resolve({  
		template: '<div>I am async!</div>'  
		})  
	}, 1000)  
})
```




#### 解析 DOM 模板时的注意事项
由于有些元素只能出现在固定的html元素内部，会导致：
	有些自定义组件会被当做无效内容而被提升到外部渲染出错。（但当模板来源为template字符串，单文件组件，`<script type="text/x-template">`时，该条限制不存在）
		可用is属性解决；





#### 父子组件通信
父组件向子组件传递数据
	父组件通过 props 向下传递数据给子组件；子组件的prop随父组件即时更新。
	静态 props：在子组件的props选项中标明要从父组件的子组件标签上获取的数据的静态值(不用bind)。子组件再像使用data数据一样使用props中传递的数据。
	动态props：获取父组件中的动态值。在父组件中使用v-bind绑定像绑定标签特性一样，将子组件要用的父组件数据值设为变量，且在父组件的data中进行变量赋值。
监听子组件事件
	子组件通过 events 给父组件发送消息；
	在子组件中使用内建的$emit（'自定义的事件名', 传递给父组件的参数）方法，在父组件中的子组件标签名中通过v-on监听该自定义事件及进行事件处理，（且由\$event访问到参数，当事件处理为函数时，则函数的第一个参数为传递参数）。可先在组件中触发emit方法的调用，然后父组件可监听到该事件并进行处理；
父子组件间的数据双向绑定
	自定义组件上使用v-moel指令（本质上语法糖）：`<base-checkbox v-model="modelValue"></base-checkbox>`
		实现父子组件的数据双向绑定：组件上的modelValue会传给prop，自定义组件上的v-model会默认会利用名为 value 的 prop 和名为 input 的事件。（本质相当于在子组件标签上同时使用v-bind（通过props传递给子组件）及v-on监听子组件emit自定义事件的变化，即props与监听emit的合用。）
		model选项：
			避免像单选框、复选框等类型的输入控件可能会将 value attribute 用于不同的目的。可在组件内添加model选项，包含prop和event。
		使用方法：
			如input元素，在子组件的input元素上，value作为prop并做绑定v-bind，再自定义input事件；

.sync 修饰符——————v-bind命令的.sync 修饰符实质就是父组件监听子组件更新某个props的请求的缩写语法，一种语法糖。vue3不支持。
	实现父子组件数据的双向绑定
		其他两种方式：
			v-model实现：vue2中：一个组件的v-model只能有一个prop，vue3中支持多个prop。适用特定的 一些表单组件；
			emit方法：父通过prop向子传，子组件通过emit触发事件给父组件发消息；
		v-bind命令的.sync修饰符方法
			使用：本质使用了在prop和emit的基础上改进(只简略了父级的处理数据更新)；如，给定需双向绑定的变量：title
				直接在子组件实例上给需绑定数据加上.sync修饰符，省略父级事件监听的书写，在子组件上prop接收，emit将事件命名为update:title，且传递被title的期望新值赋值了的变量。(prop数据不可变更)。
			内部实现
				第一步，父组件的子组件实例上< v-bind:title=’XX‘ @自定义事件名=’父组件处理title的更新‘ > ,改为< v-bind:title=’XX‘ @update:title=’父组件处理值的更新’  >；
				第二步，父组件的子组件实例上数据后加.sync修饰,再省略父组件监听子组件事件的书写，见< v-bind:title.sync='XX'  >，

#### 自定义事件
事件名：始终使用 kebab-case 的事件名；
将原生事件绑定到组件，三种方法：
	1. 当父元素监听原生事件的目标元素为组件的根元素时，使用在组件实例上的v-on 原生事件后使用 .native 修饰符：父元素将监听组件的根元素上的原生事件。但当子组件根元素无法触发该事件时，父级的 `.native` 监听器将静默失败。将监听失败。
					<BaseInput1 @focus.native="onFocus" v-model="value"/>
	2. $listeners对象，当父元素想要监听事件的目标元素不在根元素上时使用。相当于把子组件当成透明包裹器了。
			在组件的目标元素上添加v-on=’$listeners‘，\$listeners包含了作用在这个组件上的所有事件监听器；已将所有的事件监听器指向这个元素。
			在子组件的v-on上也可以自定义监听器，或覆盖重写监听器。
			可配合$attr或v-model一起使用。
	3. 使用$emit，缺点：无法同时监听多个事件，处理比较麻烦。



#### 插槽
指占坑，在组件模板中占好位置，当使用组件标签时，父元素给组件标签中的内容会自动填入slot位置中，若组件内部无slot，则该内容被丢弃；
作用域（可使用父级作用域，子组件不可）
	组件标签< user-vue>xxx </user-vue>中间可以使用父元素中的数据，但不可以使用组件内部的数据，包括标签的元素属性title、name等；
		**父级模板里的所有内容都是在父级作用域中编译的；子模板里的所有内容都是在子作用域中编译的。**
后备内容（默认内容）
	没有给插槽提供内容时，可设置插槽默认内容且可被渲染。提供了则会替换默认内容；
具名插槽
	当需要把组件标签中的内容分别传给内部多个插槽时，提供插槽名name；
	用法：
		给组件内部多处的slot标签加上name属性值< slot name="xx">;    无name的slot为默认default；
		在父元素的组件标签上将内容分别用 < template v-slot：xx>标签包裹，无v-slot template包裹的内容放在default的slot里；
作用域插槽
	当插槽（组件标签中的内容）想要使用组件内部的数据时；
	用法：
		在组件内slot标签上v-bind绑定该数据；绑定在slot元素上的属性称为插槽prop，可自定义名字。     < slot v-bind:user="user">
		在父元素的组件标签内template的v-slot指令name后赋上插槽 prop名；                            < template v-slot:default="slotProps">
		在组件标签中通过插槽prop使用该组件内的数据。
独占默认插槽的缩写语法
	当组件内只有一个默认插槽时；
	组件标签的两种简写方式：
		组件标签省略template，v-slot用在组件标签上；
		v-slot省略name；                                                              < current-user v-slot="slotProps">{{ slotProps.firstName }}</current-user>
解构插槽 Prop
	插槽 slotprop 本质上是一个函数的参数列表，所以slotprop可以是一个表达式。
	用法
		在v-slot中直接展示slotprop中的变量名：v-slot=" {user} "   代替v-slot="slotprop"；
		给slotprop中的变量名重命名：v-slot=" {user：person} "
		给slotprop中的变量设置默认值：v-slot="{ user = { firstName: 'Guest' } }"
动态插槽名
	父元素上v-slot的插槽名可以是动态指令参数（一个表达式）；
具名插槽的缩写
	当存在插槽名的时候可以缩写， v-slot: name   替换成     \#name
其他示例
	在允许父组件通过插槽自定义一些可复用的组件用在子组件内部，而又不影响父子组件的数据逻辑的封装。
	用法：在子组件内部使用v-for循环渲染时列表 < li>时，想绕过子组件为 li 添加更多的功能时，可通过父元素的插槽实现。同时将子组件的数据传给子组件标签中，再作用于子组件。
废弃的语法：组件标签内部用slot表示插槽名、接收插槽prop的slot-scope；





#### 处理边界情况
访问元素和组件
	访问根实例（小型应用）
		在每个 `new Vue` 实例的子组件中，可通过`$root` property访问根实例（`new Vue` 实例）：this.$root.property；
	访问父级组件实例（不建议，难维护和理解）
		通过`$parent` property访问：this.$parent.property;
	访问子组件实例或子元素 $refs
		除了prop 和事件情况外，当需要在 JavaScript 里直接访问一个子组件时，
		如在父元素中访问子组件实例：在子组件标签上为ref属性赋值（一个 ID 引用），即ref="usernameInput"，
		然后可在父级里，使用 this.$refs. usernameInput 访问子组件实例；？
	依赖注入
		用处：为了在深层次嵌套的后代组件中访问父级组件实例，
		用法：
			可在父级组件中的provide选项中提供希望后代组件访问的数据和方法，然后在任何后代组件的inject选项中接收这些数据和方法；
		对比parent只能访上一层；
		缺点：
			提供的 property 是非响应式的；
			组件耦合了，重构困难；
程序化的事件侦听器
	通过 $on(eventName, eventHandler) 侦听一个事件
	通过 $once(eventName, eventHandler) 一次性侦听一个事件
	通过 $off(eventName, eventHandler) 停止侦听一个事件

循环引用
	递归组件
		组件的模板中调用自身组件；通过name选项；Vue.component全局注册组件时，组件的name选项会自动设置为本组件名；
		递归调用时注意无限循环；
	组件之间的循环引用
		注意在模块系统依赖或导入组件时涉及组件间的循环引用，
模板定义的替代品
	内联模板 inline-template，（不建议，作用域混乱）
		在子组件标签上加上inline-template属性时，（类似内联样式），子组件将不再使用内部template中的作为模板，而是直接使用子组件标签中的元素作为模板，同时也不会作为插槽。
	X-Template
		定义组件模板的另一种方式。   < script type="text/x-template" id="hello-world-template">
		在`<script>` 元素内部书写html，在script元素标签上添加 `text/x-template` 的类型，和id名，再在组件的template引用该id；x-template 需要定义在 Vue 所属的 DOM 元素外。
控制更新
	强制更新
		vue是响应式的，可随时更新；偶有例外需要手动强制更新时，使用$forceUpdate ；
	通过 v-once 创建低开销的静态组件——不建议
		当想要快速渲染包含大量静态内容的组件时，可以在根元素上添加 `v-once` attribute 以确保这些内容只计算一次然后缓存起来；







### 过渡和动画

#### 进入/离开 & 列表过渡
vue在插入、更新或者移除 DOM 时，提供不同方式的应用过渡效果，包括以下工具：
	在 CSS 过渡和动画中自动应用 class    ————最常用
	可以配合使用第三方 CSS 动画库，如 Animate.css
	在过渡钩子函数中使用 JavaScript 直接操作 DOM
	可以配合使用第三方 JavaScript 动画库，如 Velocity.js

单元素/组件的过渡
	vue提供了内置的过渡封装组件< transition name="fade">< p>< /p>< /transition>，该组件用于包裹要实现过渡效果的组件。当以下情况时可用；
		条件渲染 (使用 v-if)
		条件展示 (使用 v-show)
		动态组件
		组件根节点
	当插入或删除包含在 transition 组件中的元素时，Vue 将会做以下处理：
			自动嗅探目标元素是否应用了 CSS 过渡或动画，如果是，在恰当的时机添加/删除 CSS 类名。
			如果过渡组件提供了 JavaScript 钩子函数，这些钩子函数将在恰当的时机被调用。
			如果没有找到 JavaScript 钩子并且也没有检测到 CSS 过渡/动画，DOM 操作 (插入/删除) 在下一帧中立即执行。(注意：此指浏览器逐帧动画机制，和 Vue 的 nextTick 概念不同)
	过渡的类名
		可用transition的name属性值替换 v；
		v-enter：
			定义进入过渡的开始状态。在元素被插入之前生效，在元素被插入之后的下一帧移除。
		v-enter-active：
			定义进入过渡生效时的状态。在整个进入过渡的阶段中应用，在元素被插入之前生效，在过渡/动画完成之后移除。这个类可以被用来定义进入过渡的过程时间，延迟和曲线函数。
		v-enter-to：
			2.1.8 版及以上定义进入过渡的结束状态。在元素被插入之后下一帧生效 (与此同时 v-enter 被移除)，在过渡/动画完成之后移除。
		v-leave：
			定义离开过渡的开始状态。在离开过渡被触发时立刻生效，下一帧被移除。
		v-leave-active：
			定义离开过渡生效时的状态。在整个离开过渡的阶段中应用，在离开过渡被触发时立刻生效，在过渡/动画完成之后移除。这个类可以被用来定义离开过渡的过程时间，延迟和曲线函数。
		v-leave-to：
			2.1.8 版及以上定义离开过渡的结束状态。在离开过渡被触发之后下一帧生效 (与此同时 v-leave 被删除)，在过渡/动画完成之后移除。
	CSS 过渡：如上，比较常用；
	CSS 动画：类似css过渡，区别是在动画中 `v-enter` 类名在节点插入 DOM 后不会立即删除，而是在 `animationend` 事件触发时删除。
	自定义过渡的类名：
		可以在transition组件标签上通过添加以下属性值来自定义过渡类名：< transition name="fade"   enter-class="xxxxx"  >
				enter-class
				enter-active-class
				enter-to-class (2.1.8+)
				leave-class
				leave-active-class
				leave-to-class
				优先级高于普通的类名
	同时使用过渡和动画
		Vue监听过渡和动画的完成，可使用事件监听器：
			transitionend 过渡
			animationend 动画
		同时使用过渡和动画时，通过type属性声明你需要 Vue 监听的类型。
	显性的过渡持续时间
		你可以用 < transition> 组件上的 duration 属性上 定制一个显性的过渡持续时间 (以毫秒计)：< transition :duration="1000">
		也可以定制进入和移出的持续时间： < transition :duration="{ enter: 500, leave: 800 }">
	JavaScript 钩子
		钩子函数可以结合 CSS `transitions/animations` 使用，也可以单独使用。
					例：配合transitions使用：
							< transition  v-on:before-enter="beforeEnter">...< />
							js:  //....，method:{ beforeEnter: function () {}  }
		当只用 JavaScript 过渡的时候，在 enter 和 leave 中必须使用 done 进行回调。否则，它们将被同步调用，过渡会立即完成。
		推荐对于仅使用 JavaScript 过渡的元素添加 `v-bind:css="false"`，Vue 会跳过 CSS 的检测。这也可以避免过渡过程中 CSS 的影响。

初始渲染的过渡
	< transition appear>，通过 appear 属性设置节点在初始渲染的过渡；
	默认和进入/离开过渡一样，同样也可以自定义 CSS 类名。
	可以自定义 JavaScript 钩子，同上；

多个元素的过渡
	同样用transition 包裹多个元素如table，或列表；
	注意：
		当有相同标签名的元素切换时，需要通过 key attribute 设置唯一的值来标记以让 Vue 区分它们，否则 Vue 为了效率只会替换相同标签内部的内容。即使在技术上没有必要，给在 < transition> 组件中的多个元素设置 key 是一个更好的实践。
	过渡模式
		用于当同时生效的进入和离开的过渡不能满足所有要求时；提供：
			in-out：新元素先进行过渡，完成之后当前元素过渡离开。
			out-in：当前元素先进行过渡，完成之后新元素过渡进入。

多个组件的过渡：可以通过使用动态组件的方式；

列表过渡
	对于渲染使用v-for的列表时进行过渡的情况，使用 < transition-group> 组件。特点为：
			该组件会以一个真实元素呈现：默认为一个 < span>。你也可以通过 tag attribute 更换为其他元素。
			过渡模式不可用，因为不再相互切换特有的元素。
			内部元素总是需要提供唯一的 key attribute 值。
			CSS 过渡的类将会应用在内部的元素中，而不是这个组/容器本身。
	列表的进入/离开过渡
		使用之前一样的 CSS 类名。
	列表的排序过渡
		可以改变定位；通过v-move 类名，它会在元素的改变定位的过程中应用。
		内部实现：Vue 使用了一个叫 FLIP 简单的动画队列，使用 transforms 将元素从之前的位置平滑过渡新的位置。
			FLIP 动画不仅可以实现单列过渡，多维网格也同样可以过渡；
	列表的交错过渡
		通过 data attribute 与 JavaScript 通信，就可以实现列表的交错过渡

可复用的过渡
	1、创建一个可复用过渡组件，该组件的模板为：< transition> 或者 < transition-group>作为根组件，再在其中放置slot；
	2、也可使用函数式组件
动态过渡
	Vue 中即使是过渡也是数据驱动的，可通过v-bind绑定name的动态值。




#### 状态过渡
针对的情况为：
		数字和运算
		颜色的显示
		SVG 节点的位置
		元素的大小和其他的 property
		这些数据要么本身就以数值形式存储，要么可以转换为数值。

更新数值时的过渡与动画：
	可用wactch侦听...
动态状态过渡



### 可复用性 & 组合

#### 混入
基础
	通过混入对象，分发 Vue 组件中的可复用功能，对象可包含任意组件选项。var mixin = { data...methods}，
	当组件使用混入对象时，所有混入对象的选项将被“混合”进入该组件本身的选项。    vue.component({ mixins:[mixin ]});
		选项合并:
			组件和混入对象含有同名选项时，这些选项将以恰当的方式进行“合并”，
			数据同名时，发生冲突时以组件数据优先。
			同名钩子函数将合并为一个数组，都将被调用，混入对象的钩子将在组件自身钩子**之前**调用。
			值为对象的选项 (如methods，components，directives) 会合并，且对象键名冲突时，取组件对象的键值对。
全局混入
	指全局注册的混入，将影响**每一个**之后单独创建的 Vue 实例；
	最好只用来为组件的自定义选项注入处理逻辑。
自定义选项合并策略
	自定义选项将使用默认策略，即简单地覆盖已有值。如果想让自定义选项以自定义逻辑合并，可以向 `Vue.config.optionMergeStrategies` 添加一个函数







#### 自定义指令
代码复用和抽象的主要形式是组件。但当需要对普通 DOM 元素进行底层操作，这时候就会用到自定义指令。
	通过Vue.directive（）注册全局自定义指令；
	组件的directives选项局部注册；
钩子函数
	一个指令定义对象可以提供如下几个钩子函数 (均为可选)：
钩子函数参数：
	指令钩子函数会被传入以下参数：





#### 渲染函数 & JSX
基础
	vue在大多数情况下使用模板来创建你的 HTML。某些情况下需深入底层使用js来创建html时，在组件中可用渲染函数render选项；
			render: function (createElement) {  
					return  createElement('h1', this.blogTitle)  
			}
			createElement（又createNodeDescription）包含的信息：Vue 页面上需要渲染什么样的节点，包括及其子节点的描述信息；称虚拟节点
虚拟 DOM
	Vue 通过建立一个**虚拟 DOM** 来追踪自己要如何改变真实 DOM；
	**虚拟 DOM**：是我们对由 Vue 组件树建立起来的整个 VNode 树的称呼。
	虚拟节点**VNode**
createElement 参数
	
深入数据对象
	VNode 数据对象中也有class，style，innerHTML，普通的 HTML attribute等；
VNode 必须唯一
	渲染函数中只能有一个vnode；当需要重复很多次的元素/组件，可以使用工厂函数来实现；
使用 JavaScript 代替模板功能
	只要在原生的 JavaScript 中可以轻松完成的操作，Vue 的渲染函数就不会提供专有的替代方法；
		模板中使用的 `v-if` 和 `v-for`，可在渲染函数中用 JavaScript 的 `if`/`else` 和 `map` 来重写；
		v-model，必须自己实现相应的逻辑；
事件 & 按键修饰符
	对于 .passive、.capture 和 .once 这些事件修饰符，Vue 提供了相应的前缀可以用于 on；
插槽
	可以通过 this.$slots 访问静态插槽的内容，每个插槽都是一个 VNode 数组；return createElement('div', this.\$slots.default)
	也可以通过 this.$scopedSlots 访问作用域插槽，每个作用域插槽都是一个返回若干 VNode 的函数;
	如果要用渲染函数向子组件中传递作用域插槽，可以利用 VNode 数据对象中的 scopedSlots 字段;
JSX
	当写了很多 `render` 函数，而对应的模板如此简单时；
	 Babel 插件可用于在 Vue 中使用 JSX 语法，在render函数中可以让我们回到更接近于模板的语法上。

函数式组件
	如上所述的组件记为functional，是无状态，无实例的；
	函数式组件只是函数，所以渲染开销也低很多。
	函数式组件：
			Vue.component('my-component', {
				  functional: true,
				  props: {
					    // ...
				  },
				  render: function (createElement, context) {                        // 提供第二个参数作为上下文
					    // ...
				  }
			})
	组件需要的一切都是通过 context 参数传递，它是一个包括如下字段的对象：
		props：提供所有 prop 的对象
		children：VNode 子节点的数组
		slots：一个函数，返回了包含所有插槽的对象
		scopedSlots：(2.6.0+) 一个暴露传入的作用域插槽的对象。也以函数形式暴露普通插槽。
		data：传递给组件的整个数据对象，作为 createElement 的第二个参数传入组件
		parent：对父组件的引用
		listeners：(2.3.0+) 一个包含了所有父组件为当前组件注册的事件监听器的对象。这是 data.on 的一个别名。
		injections：(2.3.0+) 如果使用了 inject 选项，则该对象包含了应当被注入的 property。

向子元素或子组件传递 attribute 和事件
	普通组件：没有被定义为 prop 的 attribute 会自动添加到组件的根元素上，将已有的同名 attribute 进行替换或与其进行智能合并。
	函数式组件：显式定义该行为；
	如果使用基于模板的函数式组件，那么还需要手动添加 attribute 和监听器；

模板编译
	底层实现：Vue 的模板实际上被编译成了渲染函数。





#### 插件
插件通常用来为 Vue 添加全局功能。插件的功能范围没有严格的限制——一般有下面几种：
	添加全局方法或者 property。如：vue-custom-element
	添加全局资源：指令/过滤器/过渡等。如 vue-touch
	通过全局混入来添加一些组件选项。如 vue-router
	添加 Vue 实例方法，通过把它们添加到 Vue.prototype 上实现。
	一个库，提供自己的 API，同时提供上面提到的一个或多个功能。如 vue-router；
使用插件
	通过全局方法 `Vue.use()` 使用插件，且调用 `new Vue()` 启动应用之前完成：
		Vue.use(MyPlugin)；
		new Vue({  })
	也可以传入一个可选的选项对象：Vue.use(MyPlugin, { someOption: true })；
	`Vue.use` 会自动阻止多次注册相同插件，即使多次调用也只会注册一次该插件。
	某些插件检测到 Vue 是可访问的全局变量时会自动调用 Vue.use()，但在像 CommonJS 这样的模块环境中，你应该始终显式地调用 `Vue.use()`
开发插件
	`install` 方法；方法的第一个参数是 `Vue` 构造器，第二个参数是一个可选的选项对象；




#### 过滤器
简单来说就是在filters过滤器里定义一个处理函数，把函数名称写在管道符 “|” 后面，它就会处理管道符 “|” 前自定义的数据，其中自定义的数据会自动成为过滤器函数的参数。
vue可以自定义过滤器，可被用于一些常见的文本格式化。过滤器应该被添加在 JavaScript 表达式的尾部，由“管道”符号指示
	可用在两个地方
		双花括号插值  ：{{ message | capitalize }}
		 v-bind 表达式 ：< div v-bind:id="rawId | formatId">< /div>
	可以在一个组件的选项中定义本地的过滤器  filters：{}
	或者在创建 Vue 实例之前全局定义过滤器：Vue.filter（）
	当全局过滤器和局部过滤器重名时，会采用局部过滤器。
过滤器函数总接收表达式的值 (之前的操作链的结果) 作为第一个参数；




### 工具

#### 单文件组件
概述
	场景一：在vue项目中，使用 `Vue.component` 来定义全局组件，紧接着用 `new Vue({ el: '#container '})` 在每个页面内指定一个容器元素。
		缺点
			可用于小规模；此时JavaScript 只被用来加强特定的视图。当在复杂项目中，完全由js驱动时：
			全局定义 ：强制要求每个 component 中的命名不得重复
			字符串模板 ： 缺乏语法高亮，在 HTML 有多行的时候，需要用到丑陋的 \
			不支持 CSS ：意味着当 HTML 和 JavaScript 组件化时，CSS 明显被遗漏
			没有构建步骤：限制只能使用 HTML 和 ES5 JavaScript，而不能使用预处理器，如 Pug (formerly Jade) 和 Babel
	场景二：文件扩展名为 .vue的单文件组件可解决；还可以使用 webpack 或 Browserify 等构建工具。
			获得：完整语法高亮、CommonJS 模块、组件作用域的 CSS；
			可以使用预处理器来构建简洁和功能更丰富的组件，比如 Pug，Babel (with ES2015 modules)，和 Stylus。
			搭配 `vue-loader` 使用 webpack，它也能为 CSS Modules 提供头等支持；
关注点分离
	将代码库划分为松散耦合的组件再将其组合 ，优于，分离成三个大的层次并将其相互交织；
	在一个组件里，其模板、逻辑和样式是内部耦合的，并且把他们搭配在一起实际上使得组件更加内聚且更可维护。
	仍然可以把 JavaScript、CSS 分离成独立的文件然后做到热重载和预编译。
```vue
				<template>  
					<div>This will be pre-compiled</div>  
				</template>  
				<script src="./my-component.js"></script>  
				<style src="./my-component.css"></style>
```
附加工具的使用
	**NPM**
	es6
	 Vue CLI 3
	 CLI 会搞定大多数工具的配置问题，同时也支持细粒度自定义配置项。
	 从零搭建你自己的构建工具，需要通过 Vue Loader 手动配置 webpack


#### 测试
框架：单元测试工具有
	Jest
		简易性的 JavaScript 测试框架。一个其独特的功能是可以为测试生成快照 (snapshot)，以提供另一种验证应用单元的方法。
	Mocha
		灵活性的 JavaScript 测试框架；
		允许选择不同的库来满足诸如侦听 (如 Sinon) 和断言 (如 Chai) 等其它常见的功能。另一个 Mocha 独特的功能是它不止可以在 Node.js 里运行测试，还可以在浏览器里运行测试。
组件测试



#### TypeScript 支持
Vue CLI 提供了内建的 TypeScript 工具支持。
静态类型系统能帮助你有效防止许多潜在的运行时错误，而且随着你的应用日渐丰满会更加显著。
通过 NPM 安装了，就不再需要任何额外的工具辅助，即可在 Vue 中使用 TypeScript 了。
推荐配置
```js
// tsconfig.json  
{  
"compilerOptions": {  
// 与 Vue 的浏览器支持保持一致  
"target": "es5",  
   // 这可以对 `this` 上的数据 property 进行更严格的推断  
"strict": true,  
   // 如果使用 webpack 2+ 或 rollup，可以利用 tree-shake:  
"module": "es2015",  
"moduleResolution": "node"  
}  
}
```
工程创建
	Vue CLI 3 可以使用 TypeScript 生成新工程。创建方式：
1. 如果没有安装 Vue CLI 就先安装：npm install --global @vue/cli
2. 创建一个新工程，并选择 "Manually select features (手动选择特性)" 选项  ：vue create my-project-name

基本用法
	要让 TypeScript 正确推断 Vue 组件选项中的类型，您需要使用 Vue.component 或 Vue.extend 定义组件
```js
import Vue from 'vue'
const Component = Vue.extend({
  // 类型推断已启用
})

const Component = {
  // 这里不会有类型推断，
  // 因为 TypeScript 不能确认这是 Vue 组件的选项
}
```

增强类型以配合插件使用
	插件可以增加 Vue 的全局/实例 property 和组件选项。在这些情况下，在 TypeScript 中制作插件需要类型声明。庆幸的是，TypeScript 有一个特性来补充现有的类型，叫做模块补充 ;
标注返回值
	因为 Vue 的声明文件天生就具有循环性，TypeScript 可能在推断某个方法的类型的时候存在困难。因此，你可能需要在 `render` 或 `computed` 里的方法上标注返回值。
标注 Prop


#### 生产环境部署
不使用构建工具
	如果用 Vue 完整独立版本，即直接用 < script> 元素引入 Vue 而不提前进行构建，请记得在生产环境下使用压缩后的版本 (vue.min.js)
使用构建工具
	
模板预编译
	最简单的方式就是使用单文件组件——相关的构建设置会自动把预编译处理好，所以构建好的代码已经包含了编译出来的渲染函数而不是原始的模板字符串。
	当使用 DOM 内模板或 JavaScript 内的字符串模板时，模板会在运行时被编译为渲染函数。通常情况下这个过程已经足够快了，但对性能敏感的应用还是最好避免这种用法。
	使用 webpack，并且喜欢分离 JavaScript 和模板文件，你可以使用 vue-template-loader，它也可以在构建过程中把模板文件转换成为 JavaScript 渲染函数。
提取组件的css
	单文件组件：CSS 会以 `<style>` 标签注入；具有一点运行时开销，使用服务端渲染，这会导致一段“无样式内容闪烁 (fouc)”；
		解决：将所有组件的 CSS 提取到同一个文件；
跟踪运行时错误
	在组件渲染时出现运行错误，错误将会被传递至全局 Vue.config.errorHandler 配置函数 (如果已设置)。利用这个钩子函数来配合错误跟踪服务是个不错的主意。比如 Sentry，它为 Vue 提供了官方集成。





### 路由vue-router
**概述**
是官方的路由管理器。通过管理不同的 URL与组件的对应关系来访问不同的内容。可以实现多视图的单页Web应用SPA；
	SPA单页面应用：
		整个应用编译之后就只有一个index.html文件；思路是一个index.html里面有一个容器router-view，在用户进行交互的时候，并不会重新加载某个界面，而是只选择把某个视图更新到容器中去显示。
		首次加载就下载完整的HTML页面和组件，切换页面时，不重新加载整个页面而只更新视图；
通过 vue 根实例中注入 router 实例，然后再注入到每个子组件，从而让整个应用都有路由功能。
路由底层原理步骤：
	(1)**监视**地址栏变化；
	(2)**查找**当前路径对应的页面组件；
	(3)将找到的页面组件**替换**到 `router-vieW` 的位置。
	
**安装**：
	CDN方式：直接引入vue-router.js这个文件使用vue-router
		<script src="/path/to/vue.js"></script>
		<script src="/path/to/vue-router.js"></script>
	NPM方式
		在VUE项目中集成（可脚手架一气呵成）：
			npm install vue-router
			在main.js中引入我们的vue-router
**项目中router结构：**
	1、main.js文件中：
			导入路由   import router from './router'
			在Vue实例中挂载创建的路由实例：new Vue({router, ......})
	2、router/index.js 文件中：
			注入插件，调用 Vue.use(VueRouter)；
			定义路由配置(包含组件映射关系)：routes=[ 映射关系 .......]；
			创建路由实例，并且传入路由映射配置;const router = new VueRouter({ routes  })
	3、在App.vue中使用路由
			**< router-link>组件**：内置的组件, 它会被渲染成一个`<a>`标签。支持用户在具有路由功能的应用中 (点击) 导航。
				作用：解决a链接引起的页面刷新；
				常见属性：
					to, 用于指定跳转的路径。
					tag，可以指定< router-link>里可以渲染成什么组件；
					replace，后退键返回不能返回到上一个页面中，无历史记录；
					active-class:  可以修改默认的名称（`<router-link>`对应的路由匹配成功时给当前元素设置的名称）。
			**< router-view>**: 是 vue-router 提供的页面显示区域;根据当前的路径, 动态渲染出不同的组件。如顶部的标题/导航, 或者底部的一些版权信息等会和< router-view>处于同一个等级。在路由切换时, 切换的是< router-view>挂载的组件, 其他内容不会发生改变。
				< router-view>渲染首页：多配置一个映射；home。。。


| this.$route：当前激活的路由的信息对象。每个对象都是局部的，可以获取当前路由的 path, name, params, query 等属性。
| this.\$router：全局的 router 实例。this.\$router 与直接使用通过 createRouter 创建的 router 实例完全相同。通过 vue 根实例中注入 router 实例，然后再注入到每个子组件，从而让整个应用都有路由功能。其中包含了很多属性和对象（比如 history 对象），想要导航到不同URL，则使用$router.push方法；任何页面也都可以调用其 push(), replace(), go() 等方法。






#### 路由模式
背景：
	浏览器无状态，切换页面都会进行请求和刷新；而用vue和vue-router时，切换页面没有请求和刷新；实质：借用了浏览器的History API来实现，可不刷新跳转；页面的状态维持在浏览器中；
使用：
	vue2：在router/index.js的路由实例中配置mode；
	vue3： `history` 参数，
vue路由的三种模式：其中SPA应用两种history 和 hash 模式(都使用浏览器自身的特性)、和vue的abstract模式；
	hash 模式（默认）：
			实质：通过锚点值( location.hash)的改变，渲染指定DOM位置的不同数据；而不刷新页面
			url带#，用 url的hash模拟完整的url；                                `js的Location对象包含url的信息，location.href获取当前页面的url；` 
			url改变，浏览器滚动到相应位置，访问历史增加记录，页面不会重新加载，不会向后端请求；
			window.location.hash属性读取 hash 值；                  
			安全，兼容所有的浏览器和服务器。
			原理：监听window的hashchange事件，并利用js实现动态改变网页内容。           `通过 location.hash 来获取和设置hash值；`
	history模式：
			展现`user/id/1` 这种模式，与hash不同无#可以自定义地址；改变url但不请求；
			利用h5的history API:pushState() 和 replaceState() 方法应用于浏览器的历史记录栈；实现url地址的改变和网页内容的改变
				pushState：历史记录堆栈顶部添加一条记录，url有变化,但是并不触发跳转，3个参数：data, title [, url]
				replaceState()：修改 History 对象的当前记录，用法与 pushState() 方法一样；
				popstate事件：如果pushState 的URL参数设置了hash，则不触发事件；pushState和replaceState不会触发事件，只有做出浏览器动作回退等才能；
			兼容性没有 hash 好；
			缺点：
				就是当改变页面地址后，强制刷新浏览器时，（如果后端没有做准备的话）会报错，因为刷新是拿当前地址去请求服务器的，如果服务器中没有相应的响应，会出现 404 页面。
	abstract模式
		用来在不支持浏览器API的环境中，充当fallback；





#### 页面跳转
使用路由模块来实现页面跳转的方式:
	方式1：声明式导航：router-link        ：内部实现为push方法
	方式2：编程式导航：this.$router.push(‘路由地址’)：      跳转到指定url，在history栈添加记录，后退会返回到上一个页面
	方式3：this.\$router.replace()：      替换当前页面           跳转到指定url，在history栈无记录，后退会返回到上上一个页面
	方式4：this.$router.go(n)：前或者向后跳转n个页面

1、**声明式导航：router-link**，自带激活时的类名, 可以做高亮
不带参数：  
```vue.js
<router-link :to="{  name||path  :'home'}">           建议用name 
```
带参数：
```vue.js
<router-link :to="{name:'home', params || query : {id:1}}">      params：url中无参数像post，query有参数像get
<router-link :to="{name:'detail', query: {item:JSON.stringify(obj)}}"></router-link>     参数为对象
$route.query|| params.propertyName  对方组件接受参数
```


2、**编程式导航：this.$router.push**
不带参数：
```js
this.$router.push({name || path:'home'})
```
带参数：
query方式
```js
this.$router.push({name || path:'home',query: {id:'1'}})
html取参: $route.query.id
script取参: this.$route.query.id
```
param方式：
```js
this.$router.push({name:'home',params: {id:'1'}})         不能用pat
html取参:$route.params.id 
script取参:this.$route.params.id
```
直接通过path传参
```js
this.$router.push({path:'/home/123'}) 
需路由配置：path: '/home/:属性名'
获取参数：this.$route.params.id
```
参数是对象
```js
接受对象参数
JS:JSON.parse(decodeURIComponent(this.$route.query.obj)) 
HTML:JSON.parse(decodeURIComponent($route.query.obj))
```





#### 动态路由匹配
根据不同的「因素」而改变站点路由列表，多用于多用户权限系统不同用户展示不同导航菜单。
实现方式：
	前端将全部路由规定好，登录时根据用户角色权限来动态展示路由；
	路由存储在数据库中，前端通过接口获取当前用户对应路由列表并进行渲染
使用：path: '/users/:id'
	**相同的组件实例将被重复使用**，**生命周期钩子不会被调用**；响应路由参数的变化：
			1、watch `$route` 对象上的任意属性；
			2、使用 beforeRouteUpdate 导航守卫，它也可以取消导航
路由配置上，也可用正则匹配；
默认所有路由是不区分大小写的：
	可用Sensitive 与 strict 路由配置；



#### 路由嵌套
< router-view>是顶层路由；
组件也可以包含自己嵌套的 `<router-view>`，不过需在路由中配置 `children`；
**以 `/` 开头的嵌套路径将被视为根路径**；
嵌套的命名路由：
	在处理命名路由时，你通常会给子路由命名；
	

#### 命名视图：
当想同时展示侧边栏和主内容时，可同时使用多个router-view；并设置components为多个组件；

#### 重定向和别名
重定向是指当用户访问 `/home` 时，URL 会被 `/` 替换，然后匹配成 `/`；
通过routes中配置redirect；导航守卫并没有应用在跳转路由上，而仅仅应用在其目标上；
可以省略 component 配置，因为它从来没有被直接访问过，所以没有组件要渲染。
	唯一的例外是嵌套路由：如果一个路由记录有 children 和 redirect 属性，它也应该有 component 属性。
也可以重定向到相对位置；
**将 `/` 别名为 `/home`，意味着当用户访问 `/home` 时，URL 仍然是 `/home`，但会被匹配为用户正在访问 `/`。**
可以自由地将 UI 结构映射到一个任意的 URL，而不受配置的嵌套结构的限制。使别名以 `/` 开头，以使嵌套路径中的路径成为绝对路径。你甚至可以将两者结合起来，用一个数组提供多个别名；


#### 路由与props
	当routes中的 `props` 设置为 `true` 时，`route.params` 将被设置为组件的 props。
	于有命名视图的路由，你必须为每个命名视图定义 `props` 配置：
当 `props` 是一个对象时，它将原样设置为组件 props。当 props 是静态的时候很有用。


#### 路由守卫
导航发生变化的时候，导航钩子主要用来拦截导航，让它完成跳转或取消：
	outer 实例身上：beforeEach(to, from, next)、afterEach;(to, from)
	单个路由中：      beforeEnter(to, from, next)
	组件内的钩子：  beforeRouteEnter(to, from, next)、beforeRouteUpdate(to, from, next)、beforeRouteLeave(to, from, next)
	参数：
			to：目标导航的路由信息对象；
			from：离开的路由信息对象；
			next：是否要进入导航，如果需要进入导航就执行 next();      ` next(false)` 用于取消导航，不会进入导航内

钩子函数内部是不能直接访问 document 的，需要通过 window 去访问；
beforeEach()：只要切换不同的导航，beforeEach 这个导航钩子就会被执行；
afterEach()： 进入导航后触发；
beforeEnter：当访问这个导航的时候，执行这个钩子函数；
beforeRouteEnter()：








### 状态管理vuex

其实就是一个为Vue.js设计的数据仓库，就是把各个组件公用的数据放到一个仓库里面进行统一的管理，这样既使得非父子组件间的数据共享变得简单明了，也让程序变得更加可维护（将数据抽离了出来）,而且只要仓库里面的数据发生了变化，在其他组件里面数据被引用的地方也会自动更新。共享的数据抽取出来，单独存放在一个`store`（仓库）；
由于状态零散地分布在许多组件和组件之间的交互中，大型应用复杂度也经常逐渐增长，提供了vuex；
应用够简单，最好不要使用 Vuex。一个简单的 store 模式就足够所需了。
单一状态树：
	用一个对象来包含整个应用中所有层级的状态（Vuex 的 `store` 对象就是一个典型的单一状态树）。
	vuex使用了单一状态树来管理应用层级的全部状态：只有一个VUEX 对象store；

Flux、Redux、Vuex ：大同小异，都是view视图——action——state；

优点：
	vuex 对数据进行了集中管理，易于开发、维护
	vuex 中的数据是响应式的，能够实时保持数据与页面的同步
使用
	`store`文件夹
	store/index.js 文件中引入，并use（vuex）；导出export default new  vuex.store{ }
	main.js中引入store，new Vue中注入全局store；即可在所有组件使用；

![[Pasted image 20230720154544.png|400]]


在store/index.js文件中，包含的属性：
	state: 存数据的地方
	actions:   包含一些方法，提交Mutations，类似对事件的触发；
	mutations:  修改数据的方法；类似事件
	getters:
	也可将四个属性分拆个四个对应的js文件中；并在indexjs中导入四个文件，并在导出的store实例中注入四个属性；


组件中需要共享的数据中；
	获取数据：写在computed中，count(){ this.$store.state.count；} 或者//  ...mapState({      countA: 'count'    })
	修改数据：
		在methods中的自定义函数中：this.$store.dispatch( 'actions中同名方法' , 修改的新值  )；再在index.js 中actions和mutation中书写更改对应数据的方法；
		**组件必须通过 action 来改变 state**：好处是，能够记录所有 store 中发生的 state 改变，同时实现能做到记录变更 (mutation)、保存状态快照、历史回滚/时光旅行的先进的调试工具。
	mapState：
		当computed中想同时获取vuex的状态和本地的数据时，使用computed:{mapState({}) 方式会使得computed中只有vuex，此时可结合扩展运算符 computed：{  ...mapState({})    function XXX  }；
	mapState函数接受数组：...mapState([ 'XXA','XXB' ]) ，只取mapState中的A，B，两个数据；
	**mapMutations、mapActions、mapGetters同理；**
	getter：当想对store中的状态进行修饰时，可通过store对象的getters属性中自定义getXX函数中修饰数据；再在组件中直接获取getXX函数

Module，store中的模块化
当store比较臃肿时，集中了大量的状态；可以分割成模块；每个module都有自己的四个属性，或者嵌套子模块；
使用
	需要将模块挂载到store中；





#### 服务端渲染



#### 安全
永远不要将不可信任的内容作为模板内容使用：
	template: \`< div>\` + userProvidedString + \`< /div>\`
允许未过滤的用户提供的内容成为 HTML、CSS 或 JavaScript 都有潜在的危险;
Vue 的安全措施


#### 深入响应式原理





### axios
是基于 Promise 的 ajax 封装库，react/vue官方推荐使用axios发ajax请求；
特点
	基于promise的异步ajax请求库
	浏览器端/node端都可以使用
	支持 Promise API。
	支持请求/响应拦截器
	支持请求取消
	请求/响应数据转换，响应数据自动转换 JSON 数据。
	批量发送多个请求
	客户端支持安全保护，免受 XSRF 攻击。

使用：
	导入
	配置：
		请求拦截：（主要用于配置token和请求数据类型）
		响应拦截（主要用于http状态码和后端自定义的code码进行全局处理），避免在组件中频繁的判断，以及code码的使用混乱。。
创建实例
	使用自定义配置创建一个 axios 实例
		axios.create([config])
请求配置
	创建请求时可以用的配置选项：
		headers
		url   必需
		method
		transformRequest：允许在向服务器发送前，修改请求数据
		transformResponse：在传递给 then/catch 前，允许修改响应数据
		headers：是即将被发送的自定义请求头
		params 是即将与请求一起发送的 URL 参数
		paramsSerializer 是一个负责 params 序列化的函数
		data 是作为请求主体被发送的数据
		timeout 指定请求超时的毫秒数(0 表示无超时时间)，超过 timeout 的时间，请求将被中断
		withCredentials 表示跨域请求时是否需要使用凭证
		adapter 允许自定义处理请求，以使测试更轻松
		auth 
			表示应该使用 HTTP 基础验证，并提供凭据，将设置一个 Authorization 头，覆写掉现有的任意使用 headers 设置的自定义 Authorization 头
			auth: {username: 'janedoe',password: 's00pers3cret'  },
		responseType 表示服务器响应的数据类型，可以是 arraybuffer、blob、document、json、text、stream
		responseEncoding 表示对响应的编码
响应结构——某个请求的响应包含以下信息
	data 由服务器提供的响应
	status 来自服务器响应的 HTTP 状态码
	statusText 来自服务器响应的 HTTP 状态信息
	headers 服务器响应的头
	config 是为请求提供的配置信息
	request 是生成当前响应的请求

配置默认值
	可以指定将被用在各个请求的配置默认值
	全局的 axios 默认值
		baseURL：  axios.defaults.baseURL = 'http://api.example.com';
		headers.common['Authorization'] = AUTH_TOKEN;
		headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
	自定义实例默认值
配置的优先顺序


拦截器
	在请求或响应被 then 或 catch 处理前拦截它们。
	添加请求拦截器：
		axios.interceptors.request.use(    1、function (config)请求前做什么   2、function (error)对请求错误做什么    )
	添加响应拦截器
		axios.interceptors.response.use(  1、function(response)对响应数据做点什么   2、function(error)  对响应错误做点什么    )
	移除拦截器
取消请求
	使用 cancel token 取消请求。
使用 application/x-www-form-urlencoded 格式
	默认情况下，axios 将 JavaScript 对象序列化为 JSON。要以 application/x-www-form-urlencoded 格式发送数据，你可以使用以下选项之一。

请求
	axios(config)：向 `axios` 传递相关配置来创建请求：
	请求方法的别名：	axios.get()...，
		使用别名方法时， url、method、data 这些属性都不必在配置中指定。
并发
	处理并发请求的助手函数：
		axios.all(iterable)
		axios.spread(callback)
