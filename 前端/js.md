
## js语言

### 简介
1. 脚本语言，一种浏览器语言，浏览器技术，页面加载时直接运行，纯文本执行，不需要编译即可转为机器语言执行。词法语法分析之后就解释执行了，是一句一句执行的；
2. 服务端环境：node.js
3. 可在浏览器、服务器、任意搭载了引擎的设备执行。 
4. js引擎(亦称js虚拟机)：v8
	- 引擎原理：引擎读取（解析）脚本
	- 引擎将脚本转化（编译）为机器语言
	- 机器代码执行
	- 接近女神的正确方法，世界微尘里，我不会喜欢你，19日
5. 浏览器中的javascript
	可做：
		1. 安全的语言，不提供对内存或cpu的访问，最初为浏览器而创建的，
		2. 可做网页操作、用户交互、web服务器相关的
		3. 可以轻松通信当前服务器。
	不可做：
		1. 访问操作系统、读写硬盘
		2. 同源策略
		3. 别的服务器弱，需远程服务器的协议。（http）
5. js的上层语言：可以有很多语言编译转化成js语言去执行。
		typescript：添加严格的数据类型，支持复杂系统的开发。

		
JavaScript 引擎：https://zh.wikipedia.org/wi...
排版引擎：https://zh.wikipedia.org/wi...

mock工具
	开源接口mock工具：https://github.com/eolinker/eoapi   （ 包含mock功能，api管理+测试功能）

js包括ecmascript规范、dom、bom

#### 手册与规范
ECMA-262 规范，明确的定义了该语言。
	- 每年发布新版本的规范 https://tc39.es/ecma262/。
	- 即将发布的规范，最前沿的功能 https://github.com/tc39/proposals
	- MDN手册
	- 兼容性表 https://caniuse.com   https://kangax.github.io/compat-table 

ecmascript 是一种标准化规范，是js的规格，js是ecmascript的实现；
es6，正式名称ecmascript2015版本的标准语言，可泛指下一代标准包括es2015、es2016,es2017等。

Babel 转码器 
	广泛使用的es6转码器。通过安装 Babel，可以用，将 ES6 代码转为 ES5 代码（默认只转换新js句法，不转化新api，可使用垫片polyfill实现），从而在老版本的浏览器执行。
	使用
		通过在项目目录中安装Babel，实现可以使用es6编写代码，不用担心现有环境是否支持。
		也可以用在浏览器环境，网页实时进行转换，会有性能影响。


#### 代码编辑器
- IDE（集成开发环境）
		管理整个项目，完整开发环境
- 轻量编辑器
		Sublime Text、Notepad++、Vim 和 Emacs 


### 基础知识
#### 引用js：
`<script>`标签夹代码插入html中任意位置。
引用独立js文件，type和language特性原始意义取消。
	浏览器会下载js文件，保存在缓存中。—节省流量，快速加载
	设置了src属性，则忽略标签中的内容
	
#### 代码结构
最好使用分号；
不要嵌套注释；

#### 严格模式（现代模式）
'use strict' 是 JavaScript 中的一种严格模式或者更严格的语法模式。启用严格模式后，代码将被强制执行更加严格的规则，从而使代码更加健壮、安全、更容易优化。
	启用 'use strict' 的方式有两种：
		在代码文件顶部添加 'use strict' 声明；
		在函数内部添加 'use strict' 声明。
浏览器中启用use strict：放在顶部，或全部放在function(){}包装器中。
当代码中存在 'use strict' 声明时，则会强制执行 JavaScript 一些可用的更严格的规则，如变量必须先声明、重复的函数参数被禁止、eval 方法中的参数必须是字符串、禁止对不可写属性进行赋值等。

使用 'use strict' 可以帮助开发人员更加严谨的编写代码，提高代码的可读性和可维护性，同时也有助于避免一些常见的编程错误和安全漏洞。

#### 变量
最好一行只声明一个变量；let、var( 老派 )声明变量；
严格模式中需先声明再使用，非严格模式下可直接声明 num=5
变量命名：
	字母、数字、$和 _ 
	首字母非数字；
	驼峰命名；
	区分大小写；
	简洁易读；
常量声明 const
	硬编码值，一般使用大写字母和下划线命名。const COL_RED
	常规命名：执行期被计算出：页面加载时间。

#### 数据类型
 8=7原始类型+1引用，js为动态类型语言，变量类型可变换。
	- 原始类型
		Number：
			常规数字、特殊数值(+-Infinity（无穷大）、NaN计算错误)
		BigInt：任意长度的整数，大于+-2^53-1的整数， 
                       90070199254740992n
		String：
			可用单、双、反引号表示，
			反引号: 扩展功能，允许字符串中嵌入变量和表达式，\`the result is ${1 + 2}\``，还可以支持字符串跨行；
		Boolean
		null：代表无、空、值未知的特殊值，非未知对象的引用。
		undefined：未被赋值。
	- 特殊类型
		Object：用于储存数据集合和更复杂的实体    ，特殊类型。
		Symbol：创建对象的唯一标识符
typeof：运算符
	typeof x返回返回参数的类型。typeof(x) =typeof x
	typeof null=object，历史遗留问题。
	typeof alert=function，alert是函数。

#### 交互
模态函数、暂停脚本执行。浏览器决定窗口外观与位置。
alert函数：alert(" ")，模态窗
prompt()函数：
	result = prompt(title, [default]);  title：input框的内容；[default]第二参数可选，为input框的初始值；result: input框的值或null。
confirm：显示信息等待用户点击确定或取消。返回true、false。
	result = confirm(question);

#### 类型转换
字符串转换：String(false)=”false“；String(null)=”null“;
数字类型转换：算数和表达式中，自动转换number。
```js
	alert( "6" / "2" )=3；
	Number("hello”) =NaN;  Number(null)=0;
	Number(undefined)=NaN; Number("123z")=NaN;
```
空字符串或仅有空格的字符串均被视为 `0`;
布尔值转换
	直观上为空(null, unfined,NaN, "")的为false，其他值为true,非空字符串总为true；


#### 运算
- %取余，**求幂，+可将其他数据类型转换为Number；
- 运算符 + 
	二元运算符（按顺序工作），其他运算符只对数字作用，且总转换为数字；2 + 2 + '1'=‘41’；  '1' + 2 + 2=‘122’；   6 - '2'=4；
	一元运算符 +，将字符串转换为数字；对数字无效；
- 赋值，返回一个值，被赋予的值；
- 逗号，a = (1 + 2, 3 + 4)，a结果为7；
- 比较运算符，参考的是js内部编码表unicode的顺序；
	- == 、!=普通相等，先把两边转化为数字后再比较。
	- === 、!== 严格相等，不做任何类型转换，直接比较；
	- null、undefined、0
		- null === undefined，false，不相等；
		- null== undefined，true，null在== 中只与undefined相等。
		- < > <= >= , null转换为数字，undefined转换为NaN；
- 或 || 运算符：附加功能：先做布尔转换，返回第一个真值的原始值，不然返回最后一个值的原始值。
- 与&&运算符同上正好相反；
- 非!x 运算符，先转换为布尔类型，再取反。
- ?? 空值合并运算符，返回两者中第一个已定义 (除了null和undeiined)的值；
	- 被用于为变量分配默认值；
	- 最好加括号使用；
	- 无括号，不能与 || 或 && 一起使用，否则触发语法错误；
- 循环：
	- while，
	- for (let i = 0; i < 3; i++){break,continue}
	- do...while
	- 多层循环，一次跳出多层循环，使用标签，
			- labelName: for (...) {
												  ...break labelName；
												}
			 - 向上寻找标签并跳出当前循环，执行下一段代码；
			 - continue同理，跳出并执行该标记循环的下一迭代；
- swich：采用的是严格相等=== ；


#### 函数
函数是一个特殊的值，不是一个结构；
- 创建函数：两者含义一致，创建一个函数并放入变量name中；
	1. 函数声明，function name(){   }
		- 尽量减少全局变量的使用，但可用于存储项目级别的数据；
		- 参数未被传递时为undefined，可设置参数默认值，function show(from, text = "no given")；
		- 函数无返回值时为undefined；
		- 警惕return换行会直接加分号；
		- 命名：
			"get…" —— 返回一个值，
			"calc…" —— 计算某些内容，
			"create…" —— 创建某些内容，
			"check…" —— 检查某些内容并返回 boolean 值，等。
		- 一个函数应只有一个功能；
	2. 函数表达式：可省函数名，
```js
let sayHi = function() {
  alert( "Hello" );
};
```
``
	3. 箭头函数
		`let func=(arg1, arg2, ..., argN) => expression;`
		 或sum=n=>a+b; 或sum=()=>a+b; 或sum=()=>{ 需return}；
		创建func函数，参数为...，对expression求值并返回其结果；
函数声明：
	js准备运行脚本时，会创建所有全局函数声明，再执行代码；严格模式下局部函数声明只能作用于局部，只对代码块内可见；
	一般用函数声明多些；
函数表达式：
	当且执行到该条语句时创建；仅当函数声明不适应时使用；
箭头函数：
	可用于主要简单的单行行为；
函数赋值，let func = sayHi;    func();   sayHi();


### 代码质量

#### 浏览器调试
暂停执行脚本：
	断点breakpoints：暂停执行
	条件断点：符合某条件时才暂停执行
	debugger；命令也可暂停执行；
	error, 如果开发者工具是打开状态，并且按钮 || 是开启的状态）
暂停并查看
	watch察看：显示任意表达式的当前值；
	call stack调用栈：显示嵌套的调用链。
	scope作用域：显示当前的变量。
		Local：当前函数中的变量
		Global 显示全局变量


#### 代码风格
语法，花括号，最好写成代码块，行的长度尽量小，缩进，通常2/4空格或tab缩进，垂直上的逻辑块空行，避免嵌套层级过高；函数位置（先调用再集中声明）。

#### 自动检查器
检查器linters，自动检查代码样式和建议；
代码检查工具：可与编辑器集成，只需启用插件并配置代码风格。
	JSLint —— 第一批检查器之一。
	JSHint —— 比 JSLint 多了更多设置。
	ESLint —— 应该是最新的一个，可自定义
		安装 Node.JS。
		 npm install -g eslint 命令（npm 是一个 JavaScript 包安装工具）安装 ESLint。
		 js项目根目录，创建名.eslintrc配置文件；
		 编辑器中启用插件



#### 注释
避免解释性注释：描述代码如何工作和做了什么；
避免代码在可读性强时的多余注释；

必要：
	整体架构描述，高层次的整体概括；
	函数的用法
	该解决方案的重要和独特巧妙时；

注释可用于一些如 JSDoc3 等文档自动生成工具：它们读取注释然后生成 HTML 文档（或者其他格式的文档）。如：
```js
/**
* 返回 x 的 n 次幂的值。
*
* @param {number} x 要改变的值。
* @param {number} n 幂数，必须是一个自然数。
* @return {number} x 的 n 次幂的值。
*/
function pow(x, n) {
...
}
```


#### 自动化测试
使用Mocha进行自动化测试。
行为驱动开发（BDD）包含：测试、文档、示例。
先规范后实现；
	测试：代码功能
	文档：`describe` 和 `it`形容代码做了什么；
	示例：展示了一个函数可以被怎样使用。如：
```js
describe("pow", function() { 
	it("raises to n-th power", function() { 
		assert.equal(pow(2, 3), 8); 
	}); 
});
```



#### Polyfill 和转译器
- 支持新代码在旧引擎中工作；
- 转译器Transpilers：解析新代码重写成旧语法结构以支持旧引 
	   擎；通常开发者会在本机中运行转译器，并将转译后代码部署到服务器；如babel，最著名的转译器之一；	   
现代项目构建系统，如 [webpack](https://webpack.js.org/)，每次修改代码时自动运行转译器，可方便地将代码转译集成到开发过程中。
- 垫片Polyfills：更新/添加新函数的脚本被称为“polyfill”；在旧引 
		 擎中声明并实现缺失的新引擎中的函数；如：
```js
if (!Math.trunc) { // 如果没有这个函数
  // 实现它
  Math.trunc = function(number) {
    // Math.ceil 和 Math.floor 存在很老的JavaScript 引擎中
    return number<0?Math.ceil(number):Math.floor(number);
  };
}
```
JavaScript是高度动态的语言，脚本可添加/修改任何函数，甚至包括内建函数。
polyfill 库：
-   [core js](https://github.com/zloirock/core-js) 支持了很多特性，允许只包含需要的特性。
-   [polyfill.io](http://polyfill.io/) 提供带有 polyfill 的脚本的服务，具体取决于特性和用户的浏览器。



### Object对象 基础知识
#### 对象
定义：用来存储键值对和更复杂的实体，包含一个属性列表；一个属性就是一个键值对（“key: value”），键(字符串或symbol)：值（任何值）
创建一个空的对象：
```js
let user = new Object(); // “构造函数” 的语法 
let user = {}; // “字面量” 的语法
```
```js
let user = {     // 一个对象
  name: "John",  // 键 "name"，值 "John"
  age: 30,        // 键 "age"，值 30
};
```
操作：随时添加属性
	获取属性
		点user.name；
		方括号 []，可从变量中获取键；user["like"], user[tmp]
	赋值；
	移除delete user.age; 
	多词的属性加引号；user["likes birds"]获取多词属性；
	逗号结尾；
	遍历对象：
```js
for (let key in user) {
  // keys
  alert( key );  // name, age, isAdmin
  // 属性键的值
  alert( user[key] ); // John, 30, true
}
```
``
	遍历对象时排序：整数属性排序，其他按创建时间排序。
- 属性命名没有任何限制可以是语言的保留字（关键字），会自动转换成字符串；
- 属性值简写；
- 属性存在性测试方法：
	- 属性不存在不报错，获取结果为undefined；
	- in操作符（防止属性的值为undefined）
		- “属性名” in  object；//  true；



#### 对象的引用和复制
对象通过引用被赋值和拷贝。变量存储的是引用，即内存地址；
- 对象的比较；地址相同才全等；
- 对象的浅拷贝与合并：
	- 遍历它的属性，复制该对象结构；
	- 复制与合并：`Object.assign(dest, [src1, src2, src3...])`；src被复制的；可合并多个对象；结果返回dest；同属性会覆盖；
- 深拷贝：面对复合对象时，就复制该属性对象的结构；如：如 [lodash](https://lodash.com/) 库的 [_.cloneDeep(obj)](https://lodash.com/docs#cloneDeep)
- 深浅拷贝区分，拷贝的内容深不深，原对象改变了还能影响新对象的值是浅拷贝，只拷贝了对象属性的引用；原对象改变了无法影响新对象是深拷贝，把所有内容都拷贝出来了，拷贝了对象属性的结构。
const声明的对象的值可改变，变量的引用是不可变的；



#### 垃圾回收
自动完成；js中内存管理概念是可达性，即可通过引用链从根访问任何值；垃圾回收：对不可达的值回收；
内部算法：
	标记所有根；
	遍历并标记其所有引用；
	再遍历所有标记的对象并标记其引用；
	删除未标记的对象；
算法优化：
	分代收集：区分新旧对象，不同频率检查；
	增量收集：拆分多份小对象集，逐一清除；
	闲时收集：cpu空闲时运行垃圾收集器；



#### 对象方法和this
添加对象的属性方法（对象之间方法可复制）
	  函数表达式user.sayHi = function() { alert("Hello!"); };
	  函数声明再赋值；
	  省略function let user = { sayHi() { alert("Hello"); } };
this：表示当前对象，内部最好不要直接引用当前对象名；
函数内部的this无调用指代时：
		严格模式：undefined；
		非严格模式：为全局对象，即window；
箭头函数对this无效；作用于上一层正常函数；



#### 构造器和操作符new
实现可重用的对象创建代码，除了箭头函数任何函数都可以用做构造器，再通过new运行；
构造函数：
	大写字母开头命名；
	只由new操作符执行；
	一般无return；有且只返回对象，若原始类型则返回this；
	执行步骤：
		创建新空对象并分配给this；
		修改this添加新属性；
		返回this；
```js
function User(name) {
  this.name = name;
  this.isAdmin = false;
}
let user = new User("Jack");
alert(user.name); // Jack
alert(user.isAdmin); // false
```
封装构建单个对象：该构造函数不能再被调用；
```js
// 创建一个函数并立即使用 new 调用它
let user = new function() {
  this.name = "John";
  this.isAdmin = false;
、
  // ……用于用户创建的其他代码
  // 也许是复杂的逻辑和语句
  // 局部变量等
};
```


#### 可选链？.
是特殊的语法结构；为了安全访问嵌套属性；
可选链前面的值为 `undefined` 或者 `null`，它会停止运算并返回 `undefined`；否则照常，和正常的引用调用一样；为了处理不确定？的对象或属性是否存在。
- 不应过度使用可选链；
- 前变量必须已声明；
- 可选链 `?.` 不能用在赋值语句的左侧。
- 形式：
	- obj?.prop                      访问属性
	- obj?.[prop]                    访问属性
	- obj.method?.()              方法调用；



#### Symbol 类型
- “symbol” 值表示唯一的标识符。即使描述相同，值唯一，互不相同；无法直接转换为字符串;
创建该类型的值： 
```js
let id = Symbol();
let id1 = Symbol("id1");// id 是描述为 "id" 的 symbol
```
- 操作：
	- 直接显示一个Symbol：id1.toString();      //  Symbol(id1)
	- 获取描述：id1.description();     //    id1
	- 添加为对象的隐藏属性：user[id] = 1;   alert(user[id]);其它代码不能意外访问或重写该属性；别的代码不知道隐藏属性的存在；
	- 对象主体中表示：[id] : 123;
	- symbol 属性不参与 `for..in` 循环。
	- [Object.assign](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/Object/assign) 会同时复制字符串和 symbol 属性;
- 全局symbol：
	全局 symbol 注册表：symbol与对应名字的列表；
	重复读取相同描述的symbol全等；
	操作：
		Symbol.for(key)：从表中按描述读取symbol（不存在则创建）；
		Symbol.keyFor(sym)：相反通过symbol获取该描述，不存在则undefined；
- 系统symbol：
	内部的许多系统symbol可以用来微调对象的各个方面；
	通过`Symbol.*` 访问，来改变一些内建行为；
- symbol 不是 100% 隐藏的，[Object.getOwnPropertySymbols(obj)](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertySymbols) 可获取所有的symbol； [Reflect.ownKeys(obj)](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/Reflect/ownKeys) 可获取返回对象的所有键包括symbol，大部分库，内建方法和语法结构都无法获取；


#### 对象——原始值转换
对象到原始值的转换，是由许多期望以原始值作为值的内建函数和运算符自动调用的。对象相加不等于新对象。

三种转换类型hint：
- 对象-> boolean：结果都是true，故忽略；没有这种转换类型，无boolean hint；
- hint：string
		- alert(obj); 
		- other[obj];
- hin：number
		- 发生在对象相减和其他运算函数时；
		- +obj，一元加法；
		- date1 - date2；
		- user1 > user2;
- hint：default
		- 运算符不确定期望值类型时；
		- 所有内建对象（除Date），在hint default时，都自动转换为number；

转换算法
- 调用 `obj[Symbol.toPrimitive](hint)` —— 带有 symbol 键 `Symbol.toPrimitive`（系统 symbol）的方法，如果这个方法存在的话；
- 否则，如果 hint 是 `"string"` —— 尝试调用优先 `obj.toString()` 或 `obj.valueOf()`，无论哪个存在。
- 否则，如果 hint 是 `"number"` 或 `"default"` —— 尝试调用优先 `obj.valueOf()` 或 `obj.toString()`，无论哪个存在。

默认下，普通对象`toString` 和 `valueOf` 方法：
-   `toString` 方法返回一个字符串 `"[object Object]"`。
-   `valueOf` 方法返回对象自身。
如果没有 `Symbol.toPrimitive` 和 `valueOf`，`toString` 将处理所有原始转换。
`Symbol.toPrimitive`必须返回原始值否则报错；`toString` 和 `valueOf` 返回对象自身会忽略并不报错；
所有这些方法都必须返回一个原始值才能工作（如果已定义）。


自定义对象如何干预转换
	- 为对象增加x[Symbol.toPrimitive]=function(hint) {...}
	- 修改`toString` 和 `valueOf` 方法


### 数据类型
#### 原始类型的方法
javaScript 允许访问字符串，数字，布尔值和 symbol 的方法和属性。
每种原始类型都有对象包装器，提供额外功能的特殊“对象包装器”，使用后即被销毁，还提供了不同的方法；
构造器 `String/Number/Boolean` 仅供内部使用；
调用不带 `new`（关键字）的 `String/Number/Boolean` 函数是可以的且有效的。（如类型转换）
null/undefined 没有任何方法；

#### 数字类型
常规数字：双精度浮点数，64位存储，其中11位存储小数点；大小不超过+-（2^53-1）；
BigInt：任意长度的整数；
数字的表示方法
	- 下划线_：1_0_000_00，无特别含义，仅为了更好的可读性；
	- 1bn、7.3bn：10亿，73亿简写；
	- 1e9，后面9个0；8e-4；
	- 十六进制； 0xff；二、八进制，分别支持`0b` 和 `0o` 前缀；其他进制应该使用函数 `parseInt`；

精度损失
存储过程中小数的精度损失，0.1，0.2相加，以及精度损失的叠加；
解决方法：.toFix(n)，舍弃并保留小数点后n位。

方法
- num.toString(base)，返回在给定 `base` 进制数字系统中 `num` 的字符串表示形式。
	- 数字直接调用方法采用双点（为了应对小数部分）：56..toString(2)
- parseInt 和 parseFloat：对字符串返回对应的数字类型；只可按顺序识别数字；否则中断或NaN；
	- parseInt(str, radix) ，解析某进制的字符串；alert( parseInt('0xff', 16) ); // 255
- Math对象：包含小型的数学函数和常量库
	- 舍入的内建函数
		- `Math.floor()`向下舍入，取邻近坐标轴左边更小的整数。
		- `Math.ceil`向上舍入，取邻近坐标轴右边更大的整数。
		- `Math.round`四舍五入，
		- `Math.trunc`（IE 浏览器不支持这个方法），直接移除小数点；
		- 舍到小数点后n位：乘除法；或`num.toFixed(n)`，四舍五入到后n位再以字符串形式返回；
	- Math.random()，返回一个从 0 到 1 的随机数
	- `Math.max(a, b, c...)` 和 `Math.min(a, b, c...)`，从任意数量的参数中返回最大值和最小值。
	- Math.pow(n, power)，n的power次幂；
- 常规数字的判断
	-  `isNaN(value)` 转为数字，是否为 `NaN`；
	-  `isFinite(value)` 转为数字，是否是常规数字；==注：==在所有数字函数中，包括 `isFinite`，空字符串或仅有空格的字符串均被视为 `0`。
	-  特殊`Object.is`比较：对一般的值等效于全等=== ；
		- 用于特殊值NaN`Object.is(NaN, NaN)`为true；
		- 用于0/-0 的比较；`Object.is(0, -0)`为false；常用在内部规范中。
- 


#### 字符串
单引号双引号、反引号（内部可用$()表示表达式、表示跨行字符串）；
\\转义字符；
- \`str\`.length ； //3                 长度是属性存在；
- str[pos]；          找不到为undefined
- str.charAt(pos);   找不到为空字符串'';
- for(  let char of 'Hello'){};    遍历字符串；
- toLowerCase() 和 toUpperCase()；改变大小写；
- 查找
	- str.indexOf(substr)，              返回坐标，否则-1；
	- str.indexOf(substr, pos)，      从第pos个位置开始查找；
	- str.lastIndexOf(substr, pos),    从字符串的末尾开始搜索到开头,以相反的顺序列出这些事件;
				- （不常用的老技巧）简写if中对 `indexOf`  的判断，用 [bitwise NOT](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_NOT) `~` 运算符（用32二进制表示并全取反), if(~str.indexOf("Widget"))
	- **str.includes(substr, pos)   ，        返回true，false；更现代
	- str.startsWith 和 str.endsWith，     返回true，false；是否以...开始结尾；
- 获取子字符串
	- **str.slice**(start [, end])：开区间，省略end则默认到结尾；负参则从尾部开数；不可首尾倒置；   较常用；
	- str.substring(start [, end])，start和end可收尾倒置；无负参；
	- str.substr(start [, length])，给定长度，可负参从结尾开始；   历史用法现不常用
- 比较（通过 [UTF-16](https://en.wikipedia.org/wiki/UTF-16) 编码顺序）
	- str.codePointAt(pos)：返回字符串中pos位置的字符的编码
	- String.fromCodePoint(code)：返回编码为code的字符；
	-  str.localeCompare(str2)，通过语言规则判断顺序，str在前面则返回负数，排在后面负数，0为相同位置；
- str.trim() —— 删除字符串前后的空格 (“trims”)。
- str.repeat(n) —— 重复字符串 n 次。
- 代理对，处理特殊符号；
- unicode规范化形式；



#### 数组
声明
- let arr = [];         
- let arr=["apple","orrge"];
- let arr= new Array(“”，“”);      最好不用。
arr[i]或arr.at(i)、最后一项arr.at(-1);
length  :  arr.length。不是数组长度，是最大索引+1；可直接截断删除元素清空数组。
二维数组，元素为一维数组。
不要用== 比较，类型不同时会直接粗暴的进行原始值转换比较；
可直接打印数组；通过引用进行复制；
可存储任何类型、可混合类型函数、可执行函数arr[3] ()；
本质上还是对象，可创建新属性，数组作为对象使用会使引擎对数组的优化特性失效。

方法   
  添加删除元素
	shift()         头部删除并返回该元素；  性能慢（需移除左移编号更新length）
	unshift()     头部添加       可多个，      性能慢
	pop()          尾部删除出栈                     快（清理索引更新length）
	push()        尾部添加        可多个         快
	toString     以逗号隔开的字符串，转换成字符串时直接去掉方括号。
	arr.splice()    删除或拼接任意元素再返回该数组，只删除时返回包含被删除元素的新数组，旧数组变更为剩下元素数组；参数为:【起始索引，删除个数，添加的元素】,可负索引。
	arr.slice()          获取子数组，【开始索引，结束索引】,不包括结束索引。无参数则复制该数组；
	arr.concat（）  将该数组与参数拼接成新数组。【参数可为数组或值】，会只复制数组参数中的元素，普通对象参数则整体添加作为[object,object]，类数组对象若具有 `Symbol.isConcatSpreadable` 属性则依次添加其中元素。
 查找元素
	 arr.indexOf（item，start）从start开找，返回所在索引或-1     
	 arr.includes（item，start）从start开找，返回true或false；       与indexOf采用=== 全等比较；   可以查找到NaN；
	 arr.lastIndexOf（item）      从末尾开始查找是否存在
 查找对象元素
	 arr.find   查找一个符合条件的对象数组并返回该对象或undefined。arr.find(function(item, index, array) {})
	 arr.findIndex    查找对象并返回该索引或-1；参数同上
	 arr.findLastIndex    从尾部查找对象，参数同上；
	 arr.filter(fn)    arr.filter(function(item, index, array) {} 。查找数组中多个符合条件的对象并返回该子对象数组。
	
 转换数组
	 arr.map(function(item, index, array) {}     对数组每个元素调用func的结果组成新数组；
	 arr.sort(fn)    对数组进行原位排序，返回数组。需额外提供比较函数fn作为参数。
	 arr.reverse()    对数组进行原位顺序颠倒，返回数组
	 str.split(delim)     根据分隔符delim将字符串分隔成数组。str.split(', '，[n]);n 第二可选参数，限制数组长度。
	 arr.join(glue)    将数组用glue符号粘合成字符串；
循环
	for（）
	for（let  fruit of  arr） 获取元素非索引 【for（let fruit in arr）只适合普通对象（属性类型复杂），不建议用在数组】；
	arr.forEach()  为每个元素都运行一个函数。arr.forEach(function(item, index, array) {}
	arr.reduce(function(accumulator, item, index, array) {}, [initial]); 对每个元素执行func并依次传递调用结果accumulator
	arr.reduceRight    同上，元素倒序执行。
	arr.some(fn)/arr.every(fn)    对每个元素执行fn，一旦fn为true则立即停止并some返回true。/  一旦fn为false则立即停止并every返回false。
判断
	Array.isArray(value)    判断是否是数组。typeof无法区分数组和对象类型；
	thisArg参数，在func中作为this；

可迭代对象
**可迭代（Iterable）** 对象是数组的泛化
	可以应用 for..of 的对象被称为 可迭代的。
	可迭代对象必须实现 Symbol.iterator 方法。
		obj[Symbol.iterator]() 的结果被称为 迭代器（iterator）。由它处理进一步的迭代过程。
		一个迭代器必须有 next() 方法，它返回一个 {done: Boolean, value: any} 对象，这里 done:true 表明迭代结束，否则 value 就是下一个值。
		Symbol.iterator 方法会被 for..of 自动调用，但我们也可以直接调用它。
		内建的可迭代对象例如字符串和数组，都实现了 Symbol.iterator。
		字符串迭代器能够识别代理对（surrogate pair）。（译注：代理对也就是 UTF-16 扩展字符。）
		有索引属性和 length 属性的对象被称为 类数组对象。这种对象可能还具有其他属性和方法，但是没有数组的内建方法。
		大多数内建方法都假设它们需要处理的是可迭代对象或者类数组对象，而不是“真正的”数组，因为这样抽象度更高。
	Array.from(obj[, mapFn, thisArg]) 将可迭代对象或类数组对象 obj 转化为真正的数组 Array，然后我们就可以对它应用数组的方法。可选参数 mapFn 和 thisArg 允许我们将函数应用到每个元素。


#### Map
像对象一样的集合，键可以为任何类型，键可以是对象。
方法
	new Map() —— 创建 map。let reMap=new Map();    let reMap=new Map([ ['com',200],['tomatoes', 350] ]);
	Object.entries(obj)    从对象处创建Map。                   let map = new Map(Object.entries(obj));
	Object.fromEntries(map或是map.entries())      从Map处创建普通对象；
	map.set(key, value) —— 根据键存储值，返回map本身。   可以链式调用：map.set().set()
	map.get(key) —— 根据键来返回值，如果 map 中不存在对应的 key，则返回 undefined。
	map.has(key) —— 如果 key 存在则返回 true，否则返回 false。
	map.delete(key) —— 删除指定键的值。
	map.clear() —— 清空 map。
	map.size —— 返回当前元素个数。
	map.SameValueZero()       比较键是否相等，类似===
 循环
	map.keys() —— 遍历并返回一个包含所有键的可迭代对象，  for(let vege of remap.keys)
	map.values() —— 遍历并返回一个包含所有值的可迭代对象，for(let vege of remap.values)
	map.entries() —— 遍历并返回一个包含所有实体 [key, value] 的可迭代对象，for..of 默认使用这个。for(let vege of remap)
	map.foreach()   内建方法。recipeMap.forEach( (value, key, map) => {alert(\`${key}: ${value}\`); });


#### Set
值的集合，没有键，值唯一不重复；
方法
	new Set(iterable) —— 创建一个 set，如果提供了一个 iterable 对象（通常是数组），将会从数组里面复制值到 set 中。
	set.add(value) —— 添加一个值，返回 set 本身
	set.delete(value) —— 删除值，如果 value 在这个方法调用的时候存在则返回 true ，否则返回 false。
	set.has(value) —— 如果 value 在 set 中，返回 true，否则返回 false。
	set.clear() —— 清空 set。
	set.size —— 返回元素个数。
 循环
	 for of  , for(let value of set）alert(value);
	 foreach,    set.foreach((value, valueAgain, set) => {alert(value);});   valueAgain是为了兼容；
	set.keys() —— 遍历并返回一个包含所有值的可迭代对象，
	set.values() —— 与 set.keys() 作用相同，这是为了兼容 Map，
	set.entries() —— 遍历并返回一个包含所有的实体 [value, value] 的可迭代对象，它的存在也是为了兼容 Map。
 
 
#### WeakMap and WeakSet（弱映射和弱集合）
数组中的对象只要数组存在，该对象则存在，即使对象没有其他引用；let john = { name: "John" };let array = [ john ];john = null;
WeakMap  
	类似于 `Map` 的集合，它仅允许对象作为键，并且一旦通过其他方式无法访问这些对象，垃圾回收便会将这些对象与其关联值一同删除。
WeakSet
	类似于 `Set` 的集合，它仅存储对象，并且一旦通过其他方式无法访问这些对象，垃圾回收便会将这些对象删除。

优点是它们对对象是弱引用，所以被它们引用的对象很容易地被垃圾收集器移除。
不支持 `clear`、`size`、`keys`、`values`等方法
`WeakMap` 和 `WeakSet` 被用作“主要”对象存储之外的“辅助”数据结构。一旦将对象从主存储器中删除，如果该对象仅被用作 `WeakMap` 或 `WeakSet` 的键，那么该对象将被自动清除。
使用场景
	额外数据的存储或者缓存；


#### Object.keys，values，entries
可用于多种数据结构；
应用于对象Object的方法         和for in一样会忽略Symbol属性；
	Object.keys(obj) —— 返回一个包含该对象所有的键的数组。                      ！	map.keys()返回的是可迭代对象；
	Object.values(obj) —— 返回一个包含该对象所有的值的数组。
	Object.entries(obj) —— 返回一个包含该对象所有 [key, value] 键值对的数组。
 Symbol属性的获取
	Object.getOwnPropertySymbols(),返回一个只包含 Symbol 类型的键的数组.
	Reflect.ownKeys(obj)，它会返回 所有 键。

当对象想应用数组的方法时
	对象———Object.entries(obj)———>数组——>应用方法———Object.fromEntries(array)—>转换成对象




#### 解构赋值
将数组或对象的内容拆分到各个变量中；原对象和数组未被改变，等同于挨个将元素赋值给变量；
等号= 右侧可以是任何可迭代对象（字符串、数组、对象等；）
数组的解构用法
	let [firstName, ,title,surname] = arr;   可按顺序跳过不需要的元素；
	用于for(let [key,value] of remap 或Object.entries(obj))
	剩余模式：用  ...rest 变量获取数组中剩余元素组成新数组；let [name1,  ...rest] = ["Julius", "Consul", "Republic"];
	数组元素不够长时，变量值为undefined；
	默认值：赋值前设置默认值 = 。let [name = "Guest", surname = "Anonymous"] = ["Julius"];  默认值可以是函数或表达式，无提供的值时才会被调用；
变量的解构
	交换变量[guest, admin] = [admin, guest]
对象的解构
	语法：let {var1, var2} = {var1:…, var2:…}
	属性和变量名相同时，变量名顺序不重要；
	可通过冒号设置解构的对象属性和变量名的映射关系,【被解构的对象属性：被赋值变量】let {width: w, height: h, title} =options;      
	可用等号= 设置默认值；冒号等号同时结合；
	剩余模式：类比数组；
嵌套格式的解构
	仿照对应的模式解构；

用于解构为函数参数           ——为了避免调用时，给可选参数写太多undefined；
	可用对象解构；提前定义一个对象解构赋值给该函数参数；
	参数希望全部使用默认值时：可赋值一个空对象；
	



#### 日期
内建对象new Date（），对象格式为 1970-01-01T00:00:00.000Z
创建日期
	创建当前日期和设=时间的对象： let  now=new Date（）；
	new Date(milliseconds即毫秒数即时间戳)        创建1970 年 1 月 1 日 UTC+0 之后经过的毫秒数（1/1000 秒）；
	new Date(datestring即时间字符串)    
参数
	无参数：创建当前时间的对象let  now=new Date（）；
	【时间戳整数（milliseconds毫秒数】），创建1970 年 1 月 1 日 UTC+0 之后经过的毫秒数（1/1000 秒）；
	【时间字符串‘2042-02-12’】new Date("2017-01-26");   自动解析；
	【年，月，日，，，毫秒】，new Date(2011, 0, 1);多余参数默认最小值；
方法      ————用new Date（）创建的当前时间是基于UTC时间的，非当地时区。
	getFullYear()   获取年份（4 位数）
	getMonth()    获取月份，从 0 到 11。
	getDate()   获取当月的具体日期，从 1 到 31；
	getHours()，getMinutes()，getSeconds()，getMilliseconds()    获取相应的时间组件。
	getDay()      获取一周中的第几天，从 `0`（星期日）到 `6`（星期六）
 以上方法返回的都是基于当前时区的时间；
获取基于UTC时间的年月日方法
	getUTCFullYear()，年
	getUTCMonth()，月
	getUTCDay() 日
	getUTCHours()，getUTCMinutes()，getUTCSeconds()，getUTCMilliseconds() 
 特殊方法
	 getTime()  获取日期的时间戳
	 getTimezoneOffset()   返回 UTC 与本地时区之间的时差，以分钟为单位
	 **Date.now()    无需创建对象，直接返回当前时间的时间戳；可作为性能优化；**
 设置日期组件
		setFullYear(year, [month], [date])     
		setMonth(month, [date])
		setDate(date)
		setHours(hour, [min], [sec], [ms])
		setMinutes(min, [sec], [ms])
		setSeconds(sec, [ms])
		setMilliseconds(ms)
		setTime(milliseconds)，设置时间戳。除此以上均有UTC变体；
 解析时间字符串
	 Date.parse(str)   【参数格式YYYY-MM-DD类似】 解析成时间戳；

特性
	时间组件的参数超范围不用管，对象会自动计算校准
	Date对象被动转为数字类型计算时，转化为时间戳；
基准测试
	对cpu耗能高的函数进行可靠的基准测试；即性能测量；
	要点：连续多次运行比较的双方，计算时间消耗差————进一步————>应重新交替运行各10次；


####  JSON 方法，toJSON
JSON表示值和对象的通用格式。json字符串：即JSON编码/序列化/字符串化/编组化/的对象；【JSON5，支持无引号键和注释，独立的库】。
JSON字符串中只有双引号、属性名称强制使用双引号，其他原有格式不变；
js提供的方法：
- JSON.stringify(obj) ：接收对象并将其转换为json字符串, 格式：{"":XX, "":XX}；可接受类型对象、数组、原始类型；忽略函数属性、Symbol类型的键值、undefined的属性
	- 额外处理对象中的函数或数组：let json = JSON.stringify(value[, replacer, space])；replacer：要编码的属性数组或函数；space：用于格式化的空格数量；
- JSON.parse(str, [reviver])  ：将 JSON 转换回对象。【字符串，可选函数 function(key,value)可对每个键值对进行调用】，当json字符串含特殊对象如Date时，采用reviewer额外处理；
- toJSON（）使用：可在对象内自定义；有的对象自带该内建方法；JSON.stringify会自动调用；



### 函数进阶内容

#### 递归和堆栈
 递归深度：最大调用次数；受限于js引擎，一般万以下是可靠的，否则对大多数引擎来说超出限制；
 递归更优雅更容易理解和维护；有时为了优化也需要重写成循环形式；任何递归都可以写成循环；
 执行上下文和堆栈；
 递归的应用：递归遍历；
链表：以对象中的对象的对象的形式表示；属性包含value、next，最后next为null；


#### Rest 参数与 Spread 语法
**如何编写支持传入任意数量参数的函数**，**以及如何将数组作为参数传递给这类函数**
无论定义，任何函数调用时都可以传入任意多的参数；
Rest 参数     放在定义中使用——将参数装到rest数组中
	用...rest 数组表示并获取并存储参数列表。
	function（...变量名args）：声明了一个数组args，将所有参数存入了该数组；只能放在参数列表末尾，且可以只收集部分剩余参数；
“arguments” 变量    定义中使用
	特殊类数组对象；支持arguments[0]直接获取函数的参数列表值；直接包含所有参数；是可迭代对象；
	不可使用数组方法，只是对象而已；
	箭头函数没有arguments对象，若有则属于外部的普通函数；

Spread 语法————函数调用时使用；
	把数组值还原成参数列表形式；内部与for of实现相同
	用法
		Math.max(...arr)；  
		同时传多个数组：Math.max(...arr1, ...arr2)；
		可同时混合常规值。ath.max(1, ...arr1, 2, ...arr2, 25)
		可合并数组。_let merged = [0, ...arr, 2, ...arr2];
		分隔字符串成字符数组；
		可操作任何可迭代对象化成逗号列表形式；
		复制 array/object （浅拷贝）：可以复制数组和对象；一般比Object.assign使用更广；

将字符串转换成数组两种方法，基本一致，细微区别
	spread语法：只适用与可迭代对象；
	Array.from(obj)函数；支持可迭代对象和类数组对象；使用更广；




#### 变量作用域，闭包
代码块，变量内部可见；
词法环境对象包括
	环境记录：存储所有局部变量作为其属性。   变量是该词法环境对象的属性；
	对外部词法环境的引用
是规范对象，存在理论层面，无法获取且操作；
js引擎可优化它：清楚未使用变量、节省内存；
函数声明
	按顺序变量未声明前不可使用为undefined；当词法环境创建时，函数声明立即变成即用型函数；
	当代码要访问一个变量时 —— 首先会搜索内部词法环境，然后搜索外部环境，然后搜索更外部的环境，以此类推，直到全局词法环境。如果在任何地方都找不到这个变量，那么在严格模式下就会报错（在非严格模式下，为了向下兼容，给未定义的变量赋值会创建一个全局变量）。

作用域：
	通过 var 创建的变量只有函数作用域，而通过 let 和 const 创建的变量既有函数作用域，也有块作用域。
	词法作用域：是指内部函数在定义的时候就决定了其外部作用域。	闭包的外部作用域是在其定义的时候已决定，而不是执行的时候。
	作用域链：由底向上查找一次查找；
**闭包**
概述
	指的就是一个引用了非自己作用域变量的函数且该变量本身作用域被销毁但因被引用还在内存中时是闭包。当两个函数彼此嵌套时，内部的函数就是闭包。
	例如在函数 A 中定义了函数 B，然后在函数外部调用函数 B，这个过程就是闭包。
	// 指一个函数可以记住其外部变量并可以访问这些变量。所有函数都是天生闭包的（只有一个例外）
一般使用场景
	在异步任务例如 timer 定时器，事件处理，Ajax 请求中被作为回调
	被外部函数作为返回结果返回，或者返回结果对象中引用该内部函数
	异步 API 比如 HTML5 Geolocation，WebSockets , requestAnimationFrame()等


垃圾收集
	如果有一个嵌套的函数在函数结束后仍可达，则它将具有引用词法环境的 `[[Environment]]` 属性。
	当词法环境对象变得不可达时，封闭的词法环境被删除；
实际开发中的优化
	V8 引擎在优化时，如果从代码中可以明显看出有未使用的外部变量，那么就会将其删除。**副作用是，此类变量在调试中将不可用。**


#### 老旧的 "var"
一般不用
“var” 
	没有块级作用域、无循环作用域：只有函数内作用域和全局作用域；
	可以反复声明，let会报错。
	变量的使用与被定义位置无关；let必须按顺序；
	存在变量声明提升：变量的声明提升到头部；
	赋值不提升；

 IIFE    ——不再使用。
 立即调用函数表达式，是模仿块级作用域的方法；创建了一个函数表达式并立即调用
 语法：( function(){} )()



#### 全局对象
提供变量和函数可以在任何地方使用；默认内建于语言或环境中；
所有属性可以直接访问；指省略全局对象名称使用；
尽量少使用全局变量
浏览器中var声明的全局函数和变量会变成全局对象的属性；
包括
	JavaScript 的内建方法，“Array”
	环境特定的值，window.innerHeight — 浏览器中的窗口高度。
实例
	浏览器全局对象名称——window    较多使用
	nodejs—————global  较多使用。
	JavaScript————globalThis 比较不常见，一般使用特定环境中的全局对象名称；
使用 polyfills 
	使用全局对象来测试一些功能，并且创建polyfills；




#### 函数对象与NFE
函数的类型————对象；
函数的属性————属性不是变量；
	functionName.name  ,值为函数名；
	functionName.length，值为入参个数；rest 参数不参与计数。
		 内省/运行时检查：在操作其他函数的函数中使用；————多态性；
	自定义属性：正常随意自定义函数的属性；
	与闭包的比较；？？
**命名函数表达式NFE**
只用在函数表达式中，不可用在函数声明中；
语法：let sayHi = function _func_(who) {}       与正常函数表达式无实际改变，let sayHi = function (who) {} 
特点
	它允许函数在内部引用自己。
	在函数外是不可见的。
作用
	防止sayHi的值被外部代码改变，函数可以可靠地调用自身的方式。




#### "new Function" 语法
允许我们将任意字符串变为函数；通过运行时通过参数传递过来的字符串创建的。
需要从服务器获取代码或者动态地从模板编译函数时才会使用。极少使用；
函数无法访问外部（outer）变量，只能访问全局变量。
创建函数
	let func = new Function ([arg1, arg2, ...argN], functionBody);
	let sum = new Function('a', 'b', 'return a + b');   alert( sum(1, 2) ); // 3
**闭包与new Function**
	闭包：使用一个特殊的属性 `[[Environment]]` 来记录函数自身的创建时的环境的函数，具体指向了函数创建时的词法环境
	需要向 `new Function` 创建出的新函数传递数据时，必须显式地通过参数进行传递。避免了与使用压缩程序而产生冲突的问题。




#### 调度：setTimeout 和 setInterval
计划调度：等待一段时间再调用函数；所有的调度方法都不能 **保证** 确切的延时。
环境内建的方法：————不在 JavaScript 的规范中
	setTimeout（）：等待一段时间在执行某函数；【函数或代码段，时间间隔毫秒默认0，某函数参数1，某函数参数2，...】
		代码段可为箭头函数；**为函数调用设定了 `this=window；`**
	setInterval（）：根据时间间隔反复执行某函数；【同上】
取消调度
	clearTimeout（timerId），timerId：setTimeout返回的定时器标识符；
	clearInterval(timerId) ，同上。
周期性调度
	setInterval和嵌套setTimeout（更灵活）
		let timerId = setTimeout(function tick() { alert('tick'); _timerId = setTimeout(tick, 2000); // (*)_ }, 2000);
		setInterval要比嵌套setTimeout实际调用间隔时间短；因为函数本身的调用消耗了时间；
垃圾回收，调度方法中的函数可防止被回收；有创建的内部引用 ；
零延时的 setTimeout：setTimeout(func，[0]):   在当前正在执行的脚本执行完成后，调度程序才会调用它.



#### 装饰器模式和转发，call/apply
透明缓存
当某函数重负载而结果稳定时，可创建一个包装器wrapper函数设立map集合存储某函数运行的值，并改写某函数。某函数的每一次运行结果都将缓存且可直接从缓存的map中获取值；包装器可用于多个函数；

对于对象方法的缓存装饰器需注意this情况的传递
对于有显示设置this的函数func来说，为了避免在调用该函数func时丢失this的传递，可以使用func.call(context，...args)或apply的方式，来调用，第一个参数context作为this，后面的继续为参数。几乎等同于func（...args）;
使用 “func.call” 设定上下文   ：func.call(context，...args)
	func.call(obj, 1, 2, 3)，显示的将第一个参数作为this的传递；
	接受参数列表；
	要注意this的上下文传递；
使用func.apply：func.apply(context, args);
	几乎与call相同，不同点：
	接受包含参数的类数组对象；
**呼叫转移**
	 将所有参数连同上下文一起传递给另一个函数；通常是使用 `apply` 完成的：
**方法借用
	_[].join.call(arguments)_；
	从一个对象中获取一个方法，并在另一个对象的上下文中“调用”它；
装饰器和函数属性
	如果原始函数有属性，装饰后的函数将不再提供这些属性；
	解决：
		存在一种创建装饰器的方法，该装饰器可保留对函数属性的访问权限，可用特殊的 `Proxy` 对象来包装函数；

多参数装饰器
	1、提供哈希函数，rest参数，将多个值合并为一个：将函数的多参数通过hash函数转为一个key，在通过map存储key对应的函数结果。需选择hash函数种类；
	（2、实现类似map的新数据结构）
	（3、嵌套map）
	



#### 函数绑定
丢失 “this”的问题：当将对象方法作为回调进行传递时，容易丢失this的指代；
场景 1：有些函数（装饰器）内部可实现该this丢失的解决方法，用func.call；
场景2：对于通用的函数（setTimeout调度函数），方法：
	使用包装函数进行调用（无法解决对象突然提前被改变）； `setTimeout(function(){user.sayHi();}, 1000);或简写 setTimeout(() => user.sayHi(), 1000);`
	 内建方法 bind，绑定this；let boundFunc = func.bind(context); boundFunc()； 将context绑定到func的this指代中，其他参数原样传递；在setimeout调度中，即使对象被重写，bound依然绑定的是对象被改变前的旧值；
		 便捷方法：bindAll：当对象有很多方法都需要传递出去，则通过循环绑定所有；
		 bind绑定参数(偶尔用): let bound = func.bind(context, [arg1], [arg2], ...);
			 只绑定参数不绑定this：partial函数；




#### 箭头函数
箭头函数是针对那些没有自己的“上下文”，但在当前上下文中起作用的短代码的
	没有 this，如果有则从外部获取；
	没有构造器，不能用new调用；
	没有 arguments
	它们也没有 super关键字，对类而言，如果有则从外部函数获取；



### 对象属性配置
####  属性标志和属性描述符
对象的每个属性除了包含值value还有三个标志，即属性标志；正常创建属性时，标志默认为true；
	writable — 如果为 true，则值可以被修改，否则它是只可读的。
	enumerable — 枚举标志，如果为 true，则会被在循环中列出，否则不会被列出。
	configurable —配置标志， 如果为 true，则此属性可以被删除，这些特性也可以被修改，否则不可以。
查询属性的标志信息
	Object.getOwnPropertyDescriptor(obj,propertyName); 返回一个 “属性描述符对象”；
			例 let descriptor = Object.getOwnPropertyDescriptor(obj, propertyName);
修改属性标志
	Object.defineProperty(obj, propertyName, descriptor),  descriptor:属性描述符对象。属性存在则更新标志，否则根据
			descriptor创建属性和标志；标志默认为false；
不可枚举
	对象的内建toString方法：一般情况下在for in循环迭代中会被略过，如果在对象中自定义一个tostring方法则会被枚举出来，此时可设置改tostring方法的enumerable标志为false，也可略过，同内建方法tosting；
	不可枚举的属性也会被 `Object.keys` 排除：
不可配置
	configurable:false     表示该属性的其他标志不可修改；并且该属性不可被删除；但值可以修改（与writable标志有关）；
		例外：对于不可配置的属性，我们可以将 `writable: true` 更改为 `false`，从而防止其值被修改（以添加另一层保护）。但无法再将writable从false改为true；
Object.defineProperties(obj, descriptors)   可以一次性定义多个属性；
Object.getOwnPropertyDescriptors (obj)      一次性获取所有属性的属性描述符；
使用实例：完整的克隆（包含所有属性symbol等及其属性描述符），可用getOwnPropertyDescriptors；

设定一个全局的密封对象
	指通过Object的一些方法可以限制对象的访问；


#### 属性的 getter 和 setter
对象的属性种类
	数据属性
	访问器属性：用于获取和设置其他属性值的函数、看似普通函数；由 “getter” 和 “setter” 方法表示；语法为：get propName() {},是平常属性的读取和赋值的底层实现；
访问器属性的描述符：
	-   **`get`** —— 一个没有参数的函数，在读取属性时工作，
	-   **`set`** —— 带有一个参数的函数，当属性被设置时调用，
	-   **`enumerable`** —— 枚举标志，
	-   **`configurable`** —— 配置标志。
defineProperty时，使用 `get` 和 `set` 来传递描述符：
多功能getter/setter：
	用作“真实”属性值的包装器，即将对象的数据属性包装在访问器的内部变量中，并且只能以此访问； _ propertyname 默认是内部属性，不可通过 obj._ propertyname直接访问；
访问器属性用途：
	通过使用 getter 和 setter 替换“正常的”数据属性，来控制和调整这些属性的行为。

### 原型，继承
原型：面向对象编程的概念；是原型链的最顶层。
prototype（原型）：
	每个对象的prototype属性，指向本对象的原型。原型可以是另一个对象或者null。   有显式或隐式的；
	它当我们创建一个对象时，JavaScript会自动为该对象设置原型，通常是通过构造函数（Constructor）或者字面量（Literal）创建对象时指定的。原型对象可以包含属性和方法，这些属性和方法可以被该对象的所有实例共享。
	间接访问和设置对象的 prototype 对象：
		Object.getPrototypeOf(obj)
		Object.setPrototypeOf(obj, anotherObj)
**__proto__**属性：
	对象具有\_\_proto\_\_**属性;
	浏览器可以通过obj.\_\_proto\_\_访问和设置对象的原型；
	不能被 for in 遍历出来，也不能被 Object.keys(obj) 查找出来。
	访问对象的 obj.__proto__ 属性，默认走的是 Object.prototype 对象上 __proto__ 属性的 get/set 方法。
	普通对象创建时，只需要将它内部的隐式引用指向 Object.prototype 对象，就能兼容 __proto__ 属性访问行为，不需要将原型隐式挂载到对象的 __proto__ 属性。

Object.prototype
	Object.prototype 的\_\_proto\_\_属性为 null；
	没有自己的原型，是所有对象的原型链的末端；是原型链的最顶层。
	该对象包含一些常用的属性和方法，这些属性和方法可以被所有对象继承和访问。常用的如下：
			toString(): 返回表示对象的字符串。默认情况下，会返回 "[object Object]"。
			hasOwnProperty(propertyName): 判断对象自身是否包含指定名称的属性，而不会检查原型链。
			isPrototypeOf(object): 判断当前对象是否是指定对象的原型。
			valueOf(): 返回对象的原始值。默认情况下，会返回对象本身。
			使用：myObject.toString()：  由于继承本质上是调用 Object.prototype 上的 toString() 方法，
	查找对象属性的过程中，会一直往上找，直到Object.prototype的方法；
原型继承
	显示继承：
			给定两个对象时：Object.setPropertyOf （obj，anatherobj）
			给定一个对象作为原型返回一个新对象：Object.create（obj）
	隐式继承：
			对象 = new 构造函数（‘  ’，‘   ’），该对象的
			js提供的内置的 constructor 函数，如 Object, Array, Boolean, String, Number 等。
普通函数：f . prototype属性，值为对象{  constructor：构造函数  }
对象的种类：
	函数对象：**用函数来模拟的类**的实现，Object 和 Function
	普通对象
创建对象的方式：两者本质相同
		对象字面量，：语法糖；进行了new 构造函数创建对象，也继承了原型
		构造函数 new；
构造函数constructor：
	有一个特殊属性 prototype

#### 原型继承
**定义**：对象有一个内部特殊的隐藏属性 `[[Prototype]]`,要么为 `null`，要么就是对另一个对象的引用。该对象被称为“原型”：
**原型继承**:  从对象中读取一个缺失的属性时，js将自动从原型中获取该属性；可继承许多属性和方法
设置对象的原型：obj1. _ proto _ =obj2;     **该方式已过时**
特点：
	原型链可以很长；
	引用不能闭环；
	原型只用于读取属性；
	obj1重写原型中的方法后，只使用本对象中已重写的该方法的实现；
	_ proto _ 只能是对象或者null；且唯一；是 `[[Prototype]]` 的因历史原因而留下来的 getter/setter；
	继承链：普通对象————>Object ————> null；
结合别的用法：
	this的指代：不受原型的影响，只取决于点号.之前的对象；
	for…in 循环，在其自身和继承的属性上进行迭代。
	obj.hasOwnProperty(key)：对象的内建方法，判断某对象的key属性是否是非继承的属性，非继承的则true；
	几乎所有其他的键/值获取方法仅对对象本身起作用，如 `Object.keys` 和 `Object.values` 等。


#### F.prototype
F.prototype   对象的构造函数的常规属性， 只在new F操作时使用；当 `F.prototype` = 对象obj，new操作符会给新对象的[ [Prototype] ]赋值obj；
	创建对象后，再改变F.prototype 的值，则二次创建的对象也随之改变，而旧对象的[ [Prototype] ]还是原来的值；
每**个函数都有prototype属性**，默认值为一个对象，且只包含一个名为constructor的属性，且值为本函数f；
					function f() {} ；//  f.prototype = { constructor: f };
	**含义：构造函数的默认原型是仅含constructor的对象，且同时构造函数创建的对象的原型也继承自仅含constructor的对象；**
用 constructor 属性创建对象：let rabbit2 = new rabbit.constructor("Black Rabbit");
	使用场景：当对象的构造器未知，又想创建另一个类似的对象则可使用该方法；通过该对象的constructor获取构造器；
操作
	可完全替换掉constructor；
	也可添加删除属性到constructor属性之后；


#### 原生的原型
Object.prototype
	obj = new Object()，Object() 构造函数自身的 `prototype` 指向一个带有 `toString` 和其他方法的一个巨大的对象。
	obj.toString() 被调用时，这个方法是从 Object.prototype 中获取的；
		let obj = {}; alert(obj.__proto__ === Object.prototype); // true 
		alert(obj.toString === obj.__proto__.toString); //true 
		alert(obj.toString === Object.prototype.toString); //true
	Object.prototype 上方的链中没有更多的 [[Prototype]]，为null；
**其他内建原型**：像 Array、Date、Function 及其他，都在 prototype 上挂载了方法；
**函数 —— 它们是内建构造器 Function 的对象**
并且它们的方法（call/apply 及其他）都取自 Function.prototype；
**基本数据类型**：并非对象，若要访问属性，则临时包装器对象将会通过内建的构造器 `String`、`Number` 和 `Boolean` 被创建。
**值 null 和 undefined** 没有对象包装器；
**更改原生原型（最好不这么做）**：例如，我们向 `String.prototype` 中添加一个方法，这个方法将对所有的字符串都是可用的；
	Polyfilling 例外：特定的 JavaScript 引擎不支持某方法时，但该方法已在js规范中；可以手动实现它，并用以填充内建原型。
**从原型中借用**：指从一个对象获取一个方法，并将其复制到另一个对象。
	例：创建类数组对象，则可能需要向其中复制一些 `Array` 方法。
		方法一：通过方法的赋值；
		方法二：将 `obj.__proto__` 设置为 `Array.prototype`



#### 原型方法，没有 __proto__ 的对象
现代的获取/设置原型的方法有
	Object.getPrototypeOf(obj) —— 返回对象 obj 的 [ [Prototype] ]。
	Object.setPrototypeOf(obj, proto) —— 将对象 obj 的 [ [Prototype] ] 设置为 proto
Object.create(proto, [descriptors]) ，创建一个空对象，且原型继承自proto，有descriptors的属性描述；
	用处：可进行强大的真正准确的复制，包括所有属性及描述；
**不能随意更改已有对象的[ [Prototype] ]，一般只在创建对象时使用**；
`__proto__` 不是对象的属性，而是 `Object.prototype` 的访问器属性；`__proto__` 是一种访问 `[[Prototype]]` 的方式，而不是 `[[prototype]]` 本身。
不推荐使用内建的的 `__proto__` getter/setter 获取/设置原型；
创建无原型对象：
	Object.create(null)；
	 `{__proto__: null}`；
	 这些对象被用作字典，以存储任意（可能是用户生成的）键。通常，对象会从 `Object.prototype` 继承内建的方法和 `__proto__` getter/setter，会占用相应的键，且可能会导致副作用。原型为 `null` 时，对象才真正是空的。

__ proto __ 不被反对的唯一的用法是在创建新对象时，将其用作属性：{ __ proto__: ... }。
obj.__ proto__ 不再作为设置或读取原型；



### 类

类是一种函数；
#### Class 基本语法
语法
	class MyClass { 
		prop = value;                // 属性 
		constructor(...) {          // 构造器 
		... } 
		method(...) {}               // method 
		get something(...) {}    // getter 方法
		set something(...) {}   // setter 方法
		[Symbol.iterator] {}      // 有计算名称（computed name）的方法（此处为 symbol） 
		  ... 
	  }
methods、getters 和 setters 都被写入了 `MyClass.prototype`。
new User("John") 被调用：
	一个新对象被创建。
	运行constructor ，进行参数赋值；
	调用其方法时，从原型中获取，如F.prototype中的一样，可以访问类中的方法；
class User {...}构造过程
	1、创建User函数，该函数成为类声明的结果；函数的代码来自于 `constructor` 方法；
	2、存储类中的方法；如 `User.prototype` 中的 `sayHi`；
类不仅仅是语法糖（与将 class 视为一种定义构造器及其原型方法的语法糖的说法相比）
	- 通过 class 创建的函数具有特殊的内部属性标记 [[IsClassConstructor]]: true。因此，它与手动创建并不完全相同；编程语言会在许多地方检查该属性。例如，与普通函数不同，必须使用 `new` 来调用它。
	- 类方法不可枚举。 类定义将 `"prototype"` 中的所有方法的 `enumerable` 标志设置为 `false`。
	- 类总是使用 `use strict`。 在类构造中的所有代码都将自动进入严格模式。
类表达式
	在一个表达式中被定义，被传递，被返回，被赋值等；let User = class {};
	类似于命名函数表达式；如果类表达式有名字，那么该名字仅在类内部可见：let User = class MyClass {sayHi() { alert(MyClass);  }}
	动态地“按需”创建类:函数中  return class { sayHi() {alert(phrase);} };
类字段
	可使用类字段制作绑定方法（针对this丢失的问题）
		对含有this关键字的方法写成类字段的形式；click = () => {alert(this.value);}     对每个对象都有独立的该方法，在内部都有一个指向此对象的 `this`；
	丢失this的其他解决方法
			1、传递一个包装函数，例如 setTimeout(() => button.click(), 1000)。
			2、将方法绑定到对象，例如在 constructor 中。
		
		
	



#### 类继承
类继承是一个类扩展另一个类的一种方式。
**语法**：class Child extends Parent {...}
**关键字 extends**
	内部实现：
		使用了很好的旧的原型机制进行工作；
		将 Rabbit.prototype.[ [Prototype] ] 设置为 Animal.prototype。
	extends 后允许任意表达式；
		如，一个生成父类的函数调用；对于高级编程模式，例如当我们根据许多条件使用函数生成类，并继承它们时来说可能很有用。
**Date.prototype.[[Prototype]] 是 Object.prototype**
**重写方法**
	可以在子类中完全重写父类的方法；
	不完全替换：
		采用super关键字：
			super.method();
			super();调用一个父类 constructor（只能在我们的 constructor 中）;
	重写 constructor
		在使用 this 之前，我们必须在 Child 的 constructor 中将父 constructor 调用为 super()。
			原因：派生构造器具有特殊的内部属性[ [ConstructorKind] ]:"derived"，该标签会影响new的行为；
		子类没有自己的构造器时会默认调用父类的构造器；且父类构造器总是会使用它自己字段的值，而不是被重写的那一个。但对于方法则是调用被重写的方法；原因：类字段和类方法在继承情况下初始化顺序不一样；

内部：
    -   方法在内部的 `[[HomeObject]]` 属性中记住了它们的类/对象。这就是 `super` 如何解析父方法的。
    -   因此，将一个带有 `super` 的方法从一个对象复制到另一个对象是不安全的。



#### 静态属性和静态方法
静态的：用static 标记，一个方法作为一个整体赋值给类；静态方法属于整个类，不属于该类任何特定对象的函数。
静态属性和方法是可被继承的。静态属性被用于当我们想要存储类级别的数据时，而不是绑定到实例。
从技术上讲，静态声明与直接给类本身赋值相同



#### 私有的和受保护的属性和方法
属性和方法分为两组：
-   **内部接口** —— 可以通过该类的其他方法访问，但不能从外部访问的方法和属性。
-   **外部接口** —— 也可以从类的外部访问的方法和属性。

两种类型的对象字段（属性和方法）：
-   公共的：可从任何地方访问。它们构成了外部接口。到目前为止，我们只使用了公共的属性和方法。
-   私有的：只能从类的内部访问。这些用于内部接口。

受保护的字段是可以被继承的；**受保护的属性通常以下划线 `_` 作为前缀。**是程序员之间有一个众所周知的约定
**新特性**：私有属性和方法应该以 `#` 开头。它们只在类的内部可被访问。
私有字段与公共字段不会发生冲突；可以同时拥有私有的 `#waterAmount` 和公共的 `waterAmount` 字段。（分别为方法和字段）
私有字段不能通过 this[name] 访问



#### 扩展内建类
内建类没有静态方法继承




#### 类检查："instanceof"
instanceof 操作符
	用于检查一个对象是否属于某个特定的 class，且考虑了继承；
语法：obj instanceof Class       属于则true；
执行过程
	有静态方法 `Symbol.hasInstance`则调用该方法；
	大多数 class 没有 `Symbol.hasInstance`，则用 `obj instanceOf Class` 检查 `Class.prototype` 是否等于 `obj` 的原型链中的原型之一

类型检查方法：
	typeof	       用于 原始数据类型	     返回值为string
	{}.toString	用于原始数据类型，内建对象，包含 Symbol.toStringTag 属性的对象，返回值为string
	instanceof	用于对象，返回值为true/false
`{}.toString` 是一种“更高级的” `typeof`。
当我们使用类的层次结构（hierarchy），并想要对该类进行检查，同时还要考虑继承时，这种场景下 `instanceof` 操作符确实很出色。



#### Mixin 模式
mixin 是一个包含可被其他类使用而无需继承的方法的类。_mixin_ 提供了实现特定行为的方法，但是我们不单独使用它，而是使用它来将这些行为添加到其他类中。



### 错误处理

#### 错误处理，"try...catch"
try { // 代码... } catch (err) { // 错误捕获 }
try...catch执行
	try...catch 仅对运行时的 error 有效：代码是有效可执行的，无语法错误；即运行时错误，即异常；
	try...catch 同步执行，计划的（scheduled）”代码中发生异常，例如在 `setTimeout` 中，不会捕获到异常；需直接包裹执行函数；
Error 对象：发生错误时，js生成error对象，再传递给catch；
	 name  名称
	 message  详细文字描述。
	 stack      当前的调用栈：用于调试目的的一个字符串，其中包含有关导致 error 的嵌套调用序列的信息。
catch 也可以忽略error；
- 可以使用 `throw` 操作符来生成自定义的 error。从技术上讲，`throw` 的参数可以是任何东西，但通常是继承自内建的 `Error` 类的 error 对象。
- 再次抛出（rethrowing）是一种错误处理的重要模式：`catch` 块通常期望并知道如何处理特定的 error 类型，因此它应该再次抛出它不知道的 error。再次抛出的错误可被外部的try catch捕获，若外部没有try catch，则脚本会被杀死；
`catch` 块实际上只处理它知道该如何处理的 error，并“跳过”所有其他的 error。
- `finally` 子句：两种情况均要执行；
- try...finally ：当我们不想在这儿处理 error（让它们 fall through），但是需要确保我们启动的处理需要被完成。
- 全局 catch
	即使我们没有 `try...catch`，大多数执行环境也允许我们设置“全局” error 处理程序来捕获“掉出（fall out）”的 error。在浏览器中，就是 `window.onerror`。
	规范中没有相关内容，但是代码的执行环境一般会提供这种机制，因为它确实很有用。例如，Node.JS 有 [`process.on("uncaughtException")`](https://nodejs.org/api/process.html#process_event_uncaughtexception)。在浏览器中，我们可以将一个函数赋值给特殊的 [window.onerror](https://developer.mozilla.org/zh/docs/Web/API/GlobalEventHandlers/onerror) 属性，该函数将在发生未捕获的 error 时执行。


#### 自定义 Error，扩展 Error

我们可以正常地从 Error 和其他内建的 error 类中进行继承。我们只需要注意 name 属性以及不要忘了调用 super。
我们可以使用 instanceof 来检查特定的 error。但有时我们有来自第三方库的 error 对象，并且在这儿没有简单的方法来获取它的类。那么可以将 name 属性用于这一类的检查。
包装异常是一项广泛应用的技术：用于处理低级别异常并创建高级别 error 而不是各种低级别 error 的函数。在上面的示例中，低级别异常有时会成为该对象的属性，例如 err.cause，但这不是严格要求的。

### promise，async/await

#### 简介：回调
js提供许多函数允许异步行为；如setTimeout、loadScript(src)加载脚本和模块；
**示例**
	loadScript('/my/script.js');将一个新的、带有给定 `src` 的、动态创建的标签 `<script src="…">` 插入到文档中；
		执行步骤：浏览器自动加载并执行这段脚本（是异步调用的）；并且loadscript后面的代码不会等到脚本加载完成才执行。
		想立即使用新脚本中的函数时：
			给loadScript添加第二个参数callback；function loadScript(src, callback) {}
			callback函数将在新脚本加载完成后才执行；     ————————基于回调”的异步编程风格；
	在回调中回调
		在loadScript的嵌套调用loadScrip(放入回调函数中)
	处理 Error
		Error 优先回调风格：加载成功时，它会调用 callback(null, script)，否则调用 callback(error)。
			第一个参数作为error保留，存在则处理错误，不存在则调用 callback(null, script)；

厄运金字塔
一种异步编程方式，包含多层循环和条件语句的嵌套调用；称为“回调地狱”或“厄运金字塔”。


#### Promise
**Promise**：将“生产者代码”和“消费者代码”连接在一起的一个特殊的 JavaScript 对象；通常被用于网络请求
生产者代码：花费它所需的任意长度时间来产出所承诺的结果；
消费者代码：获得生产者代码的结果，将结果向所有订阅了的代码开放；
Promise 对象的构造器（constructor）语法：
	let promise = new Promise(function(resolve, reject) {
		// executor（生产者代码，“歌手”）
	});
	说明：
		当 `new Promise` 被创建，executor 会自动运行；
		resolve(value) —— 如果任务成功完成并带有结果 value。
		reject(error) —— 如果出现了 error，error 即为 error 对象。
		由 new Promise 构造器返回的 promise 对象具有以下内部属性：
			state：最初是pending，resolve调用后变为fulfilled，reject调用后则变成rejected；
			result：最初undefined，resolve调用后变为value，reject调用后则变成error；
		一个 resolved 或 rejected 的 promise 都会被称为 “settled”。
		executor 只能调用一个 `resolve` 或一个 `reject`。任何状态的更改都是最终的。其他多余的调用会忽略；
		`resolve/reject` 只需要一个参数（或不包含任何参数）
		还可以立即调用 `resolve` 或 `reject`；
		`state` 和 `result` 属性都是内部的，无法直接访问；但可以使用`.then`/`.catch`/`.finally` 方法
	**消费者：then，catch**
		通过使用 .then 和 .catch 方法注册消费函数。
		promise.then(func1{} , func2{} );
			func1{}: promise resolved 后且接受到结果后执行；
			func2{}：promise rejected后且接收到error信息后执行；
			只针对error：则func1设为null:   .then(null, f)
		promise.catch(f)  
			只判断错误情况；
	清理：finally
		.finally() 无论promise是否执行成功都会执行；但finally没有参数也没有返回内容即使有也会被忽略，promise的结果传递给下一个程序处理；finally本身的error将交给最近的处理程序；

**promise与回调**
回调：1、调用loadscript前必须有个知道如何处理结果的callback函数可供使用；2、只能有一个回调；
promise：1、可按自然顺序编写：先loadscript后then；2、可以多次连续调用 `.then`。

#### Promise 链
promise 链，一个接一个的执行，向下增长，不是向右增长；
	new promise(f{}).then(f{}).then(f{})：在链上依次传递上一个result；
	每个then都可以创建并返回一个thenable对象，一个具有方法 `.then` 的任意对象。它会被当做一个 promise 来对待。（这个特性允许我们将自定义的对象与 promise 链集成在一起，而不必继承自 `Promise`。）
独立地对同一个promise调用.then;
	非链式，每个then都获取同一个result；
**更复杂的示例：fetch**
作为一个好的做法，异步行为应该始终返回一个 promise。
如果 `.then`（或 `catch/finally` 都可以）处理程序返回一个 promise，那么链的其余部分将会等待，直到它状态变为 settled。当它被 settled 后，其 result（或 error）将被进一步传递下去。



#### 使用 promise 进行错误处理
.catch处理promise中的各种错误，包括reject() 调用的，或者处理程序中抛出的error；
	当一个 promise 被 reject 时，控制权将移交至最近的 rejection 处理程序。
	如果给定 `.then` 的第二个参数（即 error 处理程序），那么 `.then` 也会以相同的方式捕获 error。
隐式 try…catch
	executor和 promise 的处理程序周围有一个“隐式的 try..catch”，如果发生异常，会被捕获，并被视为 rejection 进行处理，如throw语句。
再次抛出（Rethrowing）
	promise可以再次抛出无法处理的error；如，在.catch中throw，则控制权会被移交到下一个最近的error处理程序，若catch处理成功error则继续调用最近的成功的.then处理程序中；
未处理的 rejection
	promise中存在未处理的rejection时，js引擎会跟踪此类error，并生成一个全局的error，控制台中会留下一个信息；浏览器中可触发unhandledrejection事件来捕获错误并获取具有error相关信息的event对象；通常此类 error 是无法恢复的；




#### Promise API
Promise 类有 6 种静态方法：
	1.  `Promise.all(promises)` —— 等待所有 promise 都 resolve 时，返回存放它们结果的数组。如果给定的任意一个 promise 为 reject，由 Promise.all 返回的 promise 就会立即 reject，那么它就会变成 `Promise.all` 的 error，所有其他 promise 的结果都会被忽略。且允许存在非promise的非常规值，按照该值原样传给结果数组；
	2.  `Promise.allSettled(promises)`（ES2020 新增方法）—— 等待所有 promise 都 settle 时，并以包含以下内容的对象数组的形式返回它们的结果：
		    `status`: `"fulfilled"` 或 `"rejected"`
		    `value`（如果 fulfilled）或 `reason`（如果 rejected）。
	3. `Promise.race(promises)` —— 等待第一个 settle 的 promise，并将其 result/error 作为结果返回。
	4. `Promise.any(promises)`（ES2021 新增方法）—— 等待第一个 fulfilled 的 promise，并将其结果作为结果返回。如果所有 promise 都 rejected，`Promise.any` 则会抛出 [`AggregateError`](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/AggregateError) 错误类型的 error 实例。
	5. `Promise.resolve(value)` —— 使用给定 value 创建一个 resolved 的 promise。
	6. `Promise.reject(error)` —— 使用给定 error 创建一个 rejected 的 promise。



#### Promisification
Promisification：指将一个接受回调的函数转换为一个返回 promise 的函数。（许多基于回调的函数或库进行转换后使用比较方便）。
promise 化函数方式
	使用promisify(f)，它接受一个需要被 promise 化的函数 f，并返回一个包装（wrapper）函数。
	调用 promisify(f) 会返回一个 f 的包装器。该包装器返回一个 promise，并将调用转发给原始的 f，并在我们自定义的回调中跟踪结果。
	




#### 微任务（Microtask）
promise 的处理程序 .then、.catch 和 .finally 都是异步的，then.....finally等后面的代码会在这些程序处理前被执行；
微任务队列（Microtask queue），一个内部队列；
	promise的`.then/catch/finally` 处理程序都会进入该队列，且只有js引擎处理完当前代码或没有别的任务运行，才开始执行队列；
如果我们需要确保一段代码在 `.then/catch/finally` 之后被执行，我们可以将它添加到链式调用的 `.then` 中。
在大多数 JavaScript 引擎中（包括浏览器和 Node.js），微任务（microtask）的概念与“事件循环（event loop）”和“宏任务（macrotasks）”紧密相关



#### async/await
async/await一种特殊的语法以更舒适的方式使用promise；
**async function**
	作为关键字修饰函数：这个函数总是返回一个 promise。其他值将自动被包装在一个 resolved 的 promise 中。
**await**
	1. 只在 async 函数内工作
	2. `await` 实际上会暂停函数的执行，直到 promise 状态变为 settled，然后以 promise 的结果继续执行。这个行为不会耗费任何 CPU 资源，因为 JavaScript 引擎可以同时处理其他任务：执行其他脚本，处理事件等。
	3. 可以对thenables对象使用await；（支持对promise兼容的，相似的）；
	4. error处理： 抛出异常 —— 就像那里调用了 `throw error` 一样。

- 当我们使用 `async/await` 时，几乎就不会用到 `.then` 了，因为 `await` 为我们处理了等待。并且我们使用常规的 `try..catch` 而不是 `.catch`。这通常（但不总是）更加方便。有些时候（例如在最外层作用域）我们不得不使用then catch；


### generator，高级iteration

#### generator
generator 是通过 generator 函数 function* f(…) {…} 创建的。
在 generator（仅在）内部，存在 yield 操作。
外部代码和 generator 可能会通过 next/yield 调用交换结果。
在现代 JavaScript 中，generator 很少被使用。但有时它们会派上用场，因为函数在执行过程中与调用代码交换数据的能力是非常独特的。而且，当然，它们非常适合创建可迭代对象。



#### 异步迭代和 generator
常规的 iterator 和 generator 可以很好地处理那些不需要花费时间来生成的的数据。




### 模块

#### 模块 (Module) 简介
模块，一个文件，一个脚本，一个模块可以包含用于特定目的的类或函数库。
	AMD —— 最古老的模块系统之一，最初由 require.js 库实现。
	CommonJS —— 为 Node.js 服务器创建的模块系统。主要在nodejs中使用；
	UMD —— 另外一个模块系统，建议作为通用的模块系统，它与 AMD 和 CommonJS 都兼容。
CommonJS 模块     let { stat, exists, readfile } = require('fs');
	整体加载`fs`模块且生成为对象；是运行时加载；
	导出：module.exports={}
	导入：require('…')   ，//是一个对象；现推荐import()动态导入；
ES6 模块：
	不是对象，通过 export 命令显式指定输出的代码，再通过 import 命令输入。
	只在编译时就加载需要的部分，效率高，因为不是对象不能引用本身；
ES6 模块的好处：
		静态加载的好处
		不再需要UMD模块格式了，将来服务器和浏览器都会支持 ES6 模块格式。目前，通过各种工具库，其实已经做到了这一点。
		将来浏览器的新 API 就能用模块格式提供，不再必须做成全局变量或者navigator对象的属性。
		不再需要对象作为命名空间（比如Math对象），未来这些功能可以通过模块提供。


模块可以相互加载
	export 关键字标记了可以从当前模块外部访问的变量和函数。
	import 关键字允许从其他模块导入功能。
模块支持特殊的关键字和功能；  `<script type="module">`、<script type="module" src="user.js"></script>
模块只通过 HTTP(s) 工作，而非本地
核心功能
	始终使用 “use strict”


**模块级作用域**
	每个模块都有自己的顶级作用域。一个模块中的顶级作用域变量和函数在其他脚本中是不可见的。对于模块，我们使用导入/导出而不是依赖全局变量。
	js文件相互使用需要分别导出和导入操作；
	html中的每个独立模块都是互相看不到的；（或者，可变量显式地分配给 `window` 的一个属性，使其成为窗口级别的全局变量，则全部可见）。
模块代码只在第一次导入时被解析
	一条规则：顶层模块代码应该用于初始化，创建模块特定的内部数据结构。如果我们需要多次调用某些东西 —— 我们应该将其以函数的形式导出。
	如模块被导入到多个文件中时，只有在第一次导入时解析执行代码，且只将计算结果传递给剩余的导入且共享；


**模块配置**
	经典的使用模式：
	1. 模块导出一些配置方法，例如一个配置对象。
	2. 在第一次导入时，我们对其进行初始化，写入其属性。可以在应用顶级脚本中进行此操作。
	3. 进一步地导入使用模块。

import.meta 对象包含关于当前模块的信息；浏览器环境中，它包含当前脚本的 URL    ；
模块中，顶级“this” 是 undefined；非模块中，顶级this是全局对象；
与常规脚本相比，拥有 type="module" 标识的脚本有一些特定于浏览器的差异。
模块脚本是延迟的
- 下载外部模块脚本 `<script type="module" src="...">` 不会阻塞 HTML 的处理，它们会与其他资源并行加载。
- 模块脚本会等到 HTML 文档完全准备就绪（即使它们很小并且比 HTML 加载速度更快），然后才会运行。
- 保持脚本的相对顺序：在文档中排在前面的脚本先执行。
Async 特性（异步脚本不会等待，准备好后会立即执行）
	非模块脚本：Async特性只适用于外部脚本；
	模块脚本：Async适用于内联脚本；
模块外部脚本
	- 导入相同文件的脚本只运行一次；
	- 如果模块脚本是从另一个源(别的网站)获取的，则远程服务器需提供表示允许获取的 header `Access-Control-Allow-Origin`。
不允许裸模块，import中必须给出源路径；
	某些环境，像 Node.js 或者打包工具（bundle tool）允许没有任何路径的裸模块，因为它们有自己的查找模块的方法和钩子（hook）来对它们进行微调。但是浏览器尚不支持裸模块。
兼容旧浏览器
	旧浏览器不理解 `type="module"`，未知类型的脚本会被忽略；可使用nomodule特性作为后备；
构建工具
	在生产环境中，出于性能和其他原因，开发者经常使用诸如 [Webpack](https://webpack.js.org/) 之类的打包工具将模块打包到一起。





#### 模块导入导出
export和import顺序可随意；

导入    import {...} from '.../../..';
	导入’命名的导出‘ 
		import {x [as y], ...} from "module"  ；
	导入’默认的导出‘
		import x from "module"
		import {default as x} from "module"
	导入所有：
	    import * as obj from "module"
	导入模块（其代码，并运行），但不要将其任何导出赋值给变量：
		import "module"

导出
	在声明一个 class/function/… 之前：
		export   [default]   class/function/variable ...
		默认的导出
			每个文件应该只有一个 export default
			导出的实体可能没有名称
			同一个文件可以同时有命名导出和默认导出
			也可以表示为 export { X as default};
			如果我们将所有东西 `*` 作为一个对象导入，那么 `default` 属性正是默认的导出：
	独立的导出：
		 export {x [as y], ...}
	重新导出
		export {x [as y], ...} from "module"
		export * from "module"（不会重新导出默认的导出）。
		export {default [as y]} from "module"（重新导出默认的导出）。
		重新导出的模块在当前文件中不可用（相比普通的import和export）
		例，开发中某些模块只作为内部的功能使用；




#### 动态导入
import() 表达式
	import(modulePath) 表达式加载模块并返回一个 promise，该 promise resolve 为一个包含其所有导出的模块对象。我们可以在代码中的任意位置调用这个表达式。
		eg.    import（modulepath）.then().catch() ;         let {hi, bye} = await import('./say.js');
	动态导入在常规脚本中工作时，它们不需要 `script type="module"`；import表达式只是语法，不可进行复制或使用call和apply；






### 杂项

#### Proxy 和 Reflect
**Proxy （代理）**
1、概述：
	代理提供了特殊的方法，可以在最底层更改或调整现有对象的行为。
	对目标对象架设一层拦截，可以对外界的访问进行过滤和改写；由Proxy来代理某些操作，即代理器；
		let proxy = new Proxy(target, handler)
			target ：（对象）要代理的目标对象；
			handler：{方法对象}  代理配置、捕捉器、定制的拦截行为；若未设置，proxy则直接通向原对象；
			对于可以设置、但没有设置拦截的操作，则直接落在目标对象上，按照原先的方式产生结果。
	不变量的限制
		对于某些对象的内部方法，捕捉器handler必须遵守的规定如返回值等；
	应用技巧
		可以将Proxy对象设置到`object.proxy`属性，从而可以在`object`对象上调用。var object = { proxy: new Proxy(target, handler) };
		也可以作为其他对象的原型对象；let obj = Object.create(proxy);
2、实例方法
	Proxy 支持的拦截操作一览：get、set等；
3、Proxy.revocable() 返回一个可取消的proxy实例；
	`Proxy.revocable()`的一个使用场景是，目标对象不允许直接访问，必须通过代理访问，一旦访问结束，就收回代理权，不允许再次访问。
4、this问题
	Proxy不是目标对象的透明代理，即使不做任何拦截行为与目标对象也不会完全一样；代理时，目标对象内部的this会指向proxy代理；
	有的原生对象的内部属性只能通过正确的this才能拿到，proxy也无法代理这些属性；如Date的getDate()，可通过绑定原始对象解决；
5、实例：Web 服务的客户
	很合适用来写 Web 服务的客户端。一个 Web 服务的接口，这个接口返回各种数据。Proxy 可以拦截这个对象的任意属性，所以不用为每一种数据写一个适配方法，只要写一个 Proxy 拦截就可以了。
6、内部局限性
	对于有些内建对象`Map`，`Set`，`Date`，`Promise`等使用了内部插槽（类似一种属性），将数据存储在内部插槽中，内部方法get、set等不能访问，因此代理无法访问；有时可通过目标对象绑定bind解决；
	类的私有字段也是通过内部插槽实现的；
	Proxy 无法拦截严格相等性检查 `===`；
	性能：基准测试（benchmark）取决于引擎，但通常使用最简单的代理访问属性所需的时间也要长几倍。实际上，这仅对某些“瓶颈”对象来说才重要。

内部插槽：用[[  ]]表示，是对象的数据成员，用来存储对象的状态；仅限于内部使用；

**Reflect**
概述
	Reflect API 旨在补充 Proxy，`Reflect` 是一个内建对象，其方法是内部方法的最小包装。
	设计目的：
		将对象的一些语言形式的内部方法放到reflect对象上；从`Reflect`对象上可以拿到语言内部的方法。
		修改某些`Object`方法的返回结果，让其变得更合理。
		让`Object`操作都变成函数行为。
		`Reflect`对象的方法与`Proxy`对象的方法一一对应，使得proxy对象可以方便的调用reflect方法，在拦截层用reflect保证目标对象原有的默认访问行为，配合proxy执行原生行为，然后再部署额外的功能。也使得proxy更加易读；
静态方法
	reflect有13个静态方法：get set apply
实例:使用 Proxy 实现观察者模式
	

#### eval ：执行代码字符串
概述
	内建函数 eval 允许执行一个代码字符串。
	语法：      
		 eval（代码块）；//返回值为最后一条语句的值；    eval代码在当前词法环境中执行，可访问改变外部变量；
	严格模式下，eval内部词法环境封闭外部不可访问它；非严格模式下，eval无内部词法环境可被外界改变内部的数据；
	现代较少用eval；且不建议；
应用
	在全局作用域中 eval 代码，可以使用 window.eval(code) 进行替代。
	此外，如果你的代码需要从外部作用域获取数据，请使用 new Function，并将数据作为参数传递给函数。




#### 柯里化（Currying）
概述
	是一种对函数进行转换的高阶技术，不会调用函数。它不仅被用于 JavaScript，还被用于其他编程语言。
	将一个函数从可调用的 `f(a, b, c)` 转换为可调用的 `f(a)(b)(c)`。将使用多个参数的一个函数转换成一系列使用一个参数的函数的技术。
	curry有不同的高阶实现；
	柯里化可以更容易的获取部分应用函数；
```js
function curry(f) { // curry(f) 执行柯里化转换
  return function(a) {           挨个固定参数计算剩余参数的函数，即生成部分应用函数；
    return function(b) {
      return f(a, b);
    };
  };
}
```
应用
	let curiedsum=curry(sum)；





#### Reference Type
概述
	Reference Type 是 ECMA 中的一个“规范类型”。我们不能直接使用它，但它被用在 JavaScript 语言内部。
	值为一个三值组合(obj, propertyname, isUseStrict)。
应用
	obj.f    访问结果是Reference Type值，不是函数；
	let hi = obj.f;     会将Reference Type 作为一个整体丢弃掉，并取其值 f；因此容易发生this丢失的问题；
	(obj, propertyname, isUseStrict)（）   在Reference type上调用（）时，会接收到关于对象和对象的方法的完整信息，然后可以设置正确的 `this`。
	






#### BigInt
概述
	一种特殊的数字类型，它提供了对任意长度整数的支持。
	创建方式
		整数后直接加n
		调用 `BigInt` 函数，参数为数字或者字符串；
运算方式
	正常使用+，-
	除号/ 向零舍弃；
	所有返回类型都是bigint
	不可以和常规数字类型混合使用；可相互显示转换使用 `BigInt()` 或者 `Number()`，
	不支持一元加法
	比较运算符：对 bigint 和 number 类型的数字进行比较没有问题：== 时可能相等，=== 则不相等
	布尔运算:类似常规数字；
	Polyfilling bigint 比较棘手，前并没有一个众所周知的好用的 polyfill。
		JSBI 库：使用 JSBI 替代原生的 bigint。但是 JSBI 在内部像使用 bigint 一样使用 number，并最大程度按照规范进行模拟，所以代码已经是准备好转换成 bigint 的了（bigint-ready）。对于不支持 bigint 的引擎，我们可以“按原样”使用此类 JSBI 代码，对于那些支持 bigint 的引擎 —— polyfill 会将调用转换为原生的 bigint。







#### Unicode —— 字符串内幕
一个字符以其十六进制 Unicode 编码的方式插入到字符串中，三种方式
	\\xXX  2位十六进制
	\\uXXXX  4位十六进制
	\\u{X…XXXXXX}    介于 `0` 和 `10FFFF`  
代理对
	使用一对 2 字节长度的字符编码，它被称为“代理对”。这些符号的长度为 `2`
变音符号和规范化
	表示形式：基础字符后跟着一个或多个“装饰”它的“标记”字符。'S\\u0307'









# 浏览器:文档，事件，接口

### Document

#### 浏览器环境，规格
概述
	主机环境提供了自己的对象和语言核心以外的函数。如，Web 浏览器提供了一种控制网页的方法。Node.JS 提供了服务器端功能
	“根”对象 window
		是 JavaScript 代码的全局对象；如调用方法，
		代表“浏览器窗口”，并提供了控制它的方法。如，查看视口宽度；
	文档对象模型（DOM）
		将所有页面内容表示为可以修改的对象。
		不仅仅用于浏览器，DOM 规范解释了文档的结构，并提供了操作文档的对象。有的非浏览器设备也使用 DOM。
		document 对象是页面的主要“入口点”。我们可以使用它来更改或创建页面上的任何内容。
	CSSOM 规范
		描述样式表和样式规则，将 CSS 表示为对象，以及读写这些对象。
		当我们修改文档的样式规则时，CSSOM 与 DOM 是一起使用的。
	浏览器对象模型（BOM）
		表示由浏览器（主机环境）提供的用于处理文档（document）之外的所有内容的其他对象。
	window对象
		DOM（文档对象模型）：document对象；
		BOM（浏览器对象模型）：navigator、screen、location、frames
		JavaScript：Object、Array、Function
		

DOM 树
概述
	对象：标签、嵌套标签、标签内的文本；
	HTML/XML 文档在浏览器内均被表示为 DOM 树。
		标签（tag）成为元素节点，并形成文档结构。
		文本（text）成为文本节点。只包含一个字符串，没有子项，总是树的叶子；
		换行、空格 、……等，HTML 中的所有东西在 DOM 中都有它的位置，甚至对注释也是如此。
		<!DOCTYPE...> : 一个dom节点，但很少触及;
		注释： **comment 节点**，被标记为 `#comment`，不显示，但 JS 可以从 DOM 中读取它。
		`document` 对象，也是dom节点，是DOM 的“入口点”。
	例外
		`<head>` 之前的空格和换行符均被忽略。
		</body>后的内容会被放置到body内的最下方；
		字符串开头/结尾处的空格，以及只有空格的文本节点，通常会被工具隐藏。
	自动修正
		浏览器遇到格式不正确的 HTML，它会在形成 DOM 时自动更正它。
		浏览器自动补齐关闭标签，填补缺失的部分；
		表格永远有 `<tbody>`，浏览器在创建 DOM 时，自动地创建了 `<tbody>`。

浏览器开发工具调试
	选中标签，esc键调出下方控制台；$0表示当前元素，上一个元素$1;
	命令 inspect(node)，引用 DOM 节点的变量。
	




#### 遍历DOM
概述
	以 `document` 对象开始实现对 DOM 的所有操作。
	顶层对树节点作为document的属性表示
		document.documentElement   ：html元素
		document.head  ：head元素
		document.body：  body元素
		document.body为null时：当脚本在head中，脚本无法访问在运行时不存在的元素。
	子节点（包含元素和文本）
			子节点：直系的子元素；
			子孙元素：子元素以及子元素的子元素；
			ele.**`childNodes`**：包括所有子节点和文本节点；
			ele.firstchild：第一个子节点 
			ele.lastchild：最后一个子节点；
			`elem.hasChildNodes()` 用于检查节点是否有子节点。
	兄弟节点**sibling**（包含元素和文本）
			nextSibling  ：下一个兄弟节点
			previousSibling：上一个兄弟节点；
	parentNode（包含元素和文本 ） ： 父节点
	**纯元素**
			children —— 仅那些作为元素节点的子代的节点。
			firstElementChild，lastElementChild —— 第一个和最后一个子元素。
			previousElementSibling，nextElementSibling —— 兄弟元素。
			parentElement —— 父元素。
	表格
		额外属性
			`<table>` 元素
					table.rows —— `<tr>` 元素的集合。
					table.caption/tHead/tFoot —— 引用元素 `<caption>，<thead>，<tfoot>`。
					table.tBodies ——` <tbody> `元素的集合
			`< thead >，<tfoot>，<tbody>`元素
					tbody.rows—— 表格内部 `<tr>`元素的集合。
			`<tr>`元素
					tr.cells —— 在给定 `<tr>` 中的 `<td>` 和 `<th> `单元格的集合。
					tr.sectionRowIndex —— 给定的 `<tr>` 在封闭的 `<thead>/<tbody>/<tfoot>` 中的位置（索引）。
					tr.rowIndex —— 在整个表格中 `<tr>`的编号（包括表格的所有行）。
			`<td>` 和 `<th>`元素
					td.cellIndex —— 在封闭的 `<tr>`中单元格的编号。
	DOM集合
		childNodes：集合、类数组对可迭代对象；并非数组；可用 for..of来迭代
		dom集合是只读、实时更新的、不要使用 for..in 来遍历集合。





#### 搜索：getElement*，querySelector*
获取页面任意元素
	document.getElementById(id)：通过元素的id特性获取元素
	id唯一
		不允许直接通过id名访问元素(如idname.style.background）

elem.querySelectorAll(css)：返回 `elem` 中与给定 CSS 选择器匹配的所有元素。可以使用任何 CSS 选择器（包括伪类）
elem.querySelector(css)：调用会返回给定 CSS 选择器的第一个元素。速度更快，简短；
集合是实时的；

在DOM中搜索元素节点
	最常用的是 `querySelector` 和 `querySelectorAll`，偶尔使用 getElement(s)By*；注意’s‘的使用；不允许直接通过id名访问元素
	elem.querySelector————————返回elem中与给定 CSS 选择器匹配的第一个元素。
	elem.querySelectorAll———————返回 `elem` 中与给定 CSS 选择器匹配的所有元素。可以使用任何 CSS 选择器。  静态集合
	document.getElementById——————通过元素的id特性获取元素，id唯一；
	document.getElementsByName(name)—返回在文档范围内具有给定 `name` 特性的元素。                                           实时集合
	elem.getElementsByTagName(tag)——查找具有给定标签的元素，并返回它们的集合。                                             实时集合
	elem.getElementsByClassName———返回具有给定CSS类的元素。                                                                           实时集合
	elem.matches(css)————————判断`elem` 与给定的 CSS 选择器是否匹配
	elem.closest(css)—————————查找与给定 CSS 选择器相匹配的最近的祖先
	如果 `elemB` 在 `elemA` 内（`elemA` 的后代）或者 `elemA==elemB`，`elemA.contains(elemB)` 将返回 true。





#### 节点属性：type，tag 和 content
DOM 节点类
	每个 DOM 节点都属于一个特定的类。这些类形成层次结构（hierarchy）。完整的属性和方法集是继承的结果。
	层次结构
		EventTarget根节点  ,为事件（包括事件本身）提供支持
			Node 类，提供通用 DOM 节点属性。`parentNode`，`nextSibling`
				Element 类—— 是 DOM 元素的基础类
						HTMLElement —— 是所有 HTML 元素的基础类
								HTMLInputElement —— `<input>` 元素的类，
								HTMLBodyElement —— `<body>` 元素的类，
								HTMLAnchorElement —— `<a> `元素的类，
				Document 类
						全局变量 `document` 就是属于这个类
				CharacterData类
						Text —— 对应于元素内部文本的类
						Comment —— 注释类
查看 DOM 节点类名
	通过对象的属性`constructor.name`
	使用 `toString` 方法
	 `instanceof` 来检查继承
`console.log(elem)` 显示元素的 DOM 树。
`console.dir(elem)` 将元素显示为 DOM 对象，非常适合探索其属性。
主要的 DOM 节点属性
		获取dom节点类型
			元素的`nodeType` 属性。元素节点值为1，文本节点3，document对象9......
		获取dom节点的标签名（标签名称始终是大写的，除非是在 XML 模式下）
			tagName，仅适用于元素节点。
			nodeName，可任意节点包括文本。
		获取文本节点内容
			 elem.`data` 和`nodeValue`
		获取元素内的文本
			`textContent`：获取元素内所有文本内容，且去掉所有tags。插入时所有特殊字符和标签均被视为文本。
		innerHTML属性
			将元素中的 HTML 获取为字符串形式。
			插入`<script>` 标签，会成为html一部分，但脚本不会执行。
			elem.innerHTML+=   ，会完全重写。移除旧内容再重新将内容加载；
		elem.outerHTML
			赋值不会修改 DOM 元素，而是将其从 DOM 中删除并在其位置插入新的 HTML。再通过查询 DOM 来获取对新元素的引用。
		`hidden`属性
			当被设置为 `true` 时，执行与 CSS `display:none` 相同的事。
大多数标准 HTML 特性（attribute）都具有相应的 DOM 属性。
HTML 特性（attribute）和 DOM 属性（property）并不总是相同的
规范中，DOM 类通过接口描述语言来描述，IDL；

![[截屏2023-07-01 下午9.58.14.png|250]]![[Pasted image 20230701222217.png|350]]





#### 特性和属性
浏览器加载页面时，解析html元素并生成dom对象。html特性和dom对象属性并不一一对应
DOM 属性
	DOM 节点是常规的 JavaScript 对象。属性和方法的行为类似：多值，大小写敏感；
	行为
			创建新属性
			创建新方法
			修改内建属性的原型
	DOM 属性是多类型的，字符串、布尔......
HTML 特性
	特点：大小写不敏感，是字符串类型；
	浏览器解析 HTML 生成dom对象时，浏览器会辨别标准的特性并以此创建dom属性；非标准特性则不会；
	获取元素的特性
			elem.hasAttribute(name) —— 检查特性是否存在。
			elem.getAttribute(name) —— 获取这个特性值。
			elem.setAttribute(name, value) —— 设置这个特性值。
			elem.removeAttribute(name) —— 移除这个特性。
			 elem.attributes 读取所有特性的集合；
	非标准的特性
		常用于将自定义的数据从 HTML 传递到 JavaScript，或者用于为 JavaScript “标记” HTML 元素。
		dataset
属性—特性同步
	当一个标准的特性被改变，对应的属性也会自动更新。（除了几个特例）反之亦然。
在大多数情况下，最好使用 DOM 属性。仅当 DOM 属性无法满足开发需求，并且我们真的需要特性时，才使用特性，例如：
我们需要一个非标准的特性。但是如果它以 data- 开头，那么我们应该使用 dataset。
我们想要读取 HTML 中“所写的”值。对应的 DOM 属性可能不同，例如 href 属性一直是一个 完整的 URL，但是我们想要的是“原始的”值。






#### 修改文档（document）
即时”创建新元素并修改现有页面内容。
创建 DOM 节点
	- `document.createElement(tag)` —— 用给定的标签创建一个元素节点，
	- `document.createTextNode(value)` —— 创建一个文本节点（很少使用），
	- `elem.cloneNode(deep)` —— 克隆元素，如果 `deep==true` 则深克隆与其后代一起克隆，false则不克隆子元素；
插入和移除节点的方法：
	- `node.append(...nodes or strings)` —— 在 `node` 末尾插入，
	- `node.prepend(...nodes or strings)` —— 在 `node` 开头插入，
	- `node.before(...nodes or strings)` —— 在 `node` 之前插入，
	- `node.after(...nodes or strings)` —— 在 `node` 之后插入，
	- `node.replaceWith(...nodes or strings)` —— 替换 `node`。
	- `node.remove()` —— 移除 `node`。
	- DocumentFragment  特殊的 DOM 节点，用作来传递节点列表的包装器（wrapper）。
	- 文本字符串被“作为文本”插入。
这里还有“旧式”的方法：
	- `parent.appendChild(node)`
	- `parent.insertBefore(node, nextSibling)`
	- `parent.removeChild(node)`
	- `parent.replaceChild(newElem, node)`
	这些方法都返回 `node`。
在 `html` 中给定一些 HTML，`elem.insertAdjacentHTML(where, html)` 会根据 `where` 的值来插入它：
	- `"beforebegin"` —— 将 `html` 插入到 `elem` 前面，
	- `"afterbegin"` —— 将 `html` 插入到 `elem` 的开头，
	- `"beforeend"` —— 将 `html` 插入到 `elem` 的末尾，
	- `"afterend"` —— 将 `html` 插入到 `elem` 后面。
`elem.insertAdjacentText` 和 `elem.insertAdjacentElement`：插入文本字符串和元素，但很少使用。
`document.write`。
	document.write(html)，将 `html` “就地马上”写入页面。`html` 字符串可以是动态生成的，可以使用 JavaScript 创建一个完整的页面并对其进行写入。**调用只在页面加载时工作。**稍后调用它，则现有文档内容将被擦除。多见于旧脚本。





#### 样式和类
JavaScript 处理样式和类的方法
两种设置元素样式的方式：
	给元素设置class ，首选
	使用style特性。
管理class
	两个 DOM 属性：
		className —— 字符串值，可以很好地管理整个类的集合。
		classList —— 具有 add/remove/toggle/contains 方法的对象，可以很好地支持单个类。
改变样式：
	elem.style.removeProperty：删除一个属性；
	`style.cssText` 进行完全的重写
计算样式
	getComputedStyle(element, [pseudo])，返回与 `style` 对象类似的，且包含了所有类的对象。只读。
		pseudo 伪元素（如果需要），例如 ::before。空字符串或无参数则意味着元素本身
计算值和解析值
	1. **计算 (computed)** 样式值是所有 CSS 规则和 CSS 继承都应用后的值，这是 CSS 级联（cascade）的结果。它看起来像 `height:1em` 或 `font-size:125%`。
	2. **解析 (resolved)** 样式值是最终应用于元素的样式值。







#### 元素大小和滚动
元素具有以下几何属性：

offsetParent —— 是最接近的 CSS 定位的祖先，或者是 td，th，table，body。
offsetLeft/offsetTop —— 是相对于 offsetParent 的左上角边缘的坐标。
offsetWidth/offsetHeight —— 元素的“外部” width/height，边框（border）尺寸计算在内。
clientLeft/clientTop —— 从元素左上角外角到左上角内角的距离。对于从左到右显示内容的操作系统来说，它们始终是左侧/顶部 border 的宽度。而对于从右到左显示内容的操作系统来说，垂直滚动条在左边，所以 clientLeft 也包括滚动条的宽度。
clientWidth/clientHeight —— 内容的 width/height，包括 padding，但不包括滚动条（scrollbar）。
scrollWidth/scrollHeight —— 内容的 width/height，就像 clientWidth/clientHeight 一样，但还包括元素的滚动出的不可见的部分。
scrollLeft/scrollTop —— 从元素的左上角开始，滚动出元素的上半部分的 width/height。
除了 scrollLeft/scrollTop 外，所有属性都是只读的。如果我们修改 scrollLeft/scrollTop，浏览器会滚动对应的元素。





#### Window 大小和滚动
几何：
	文档可见部分的 width/height（内容区域的 width/height）：document.documentElement.clientWidth/clientHeight
	整个文档的 width/height，其中包括滚动出去的部分：
滚动：
	读取当前的滚动：window.pageYOffset/pageXOffset。
	更改当前的滚动：
		window.scrollTo(pageX,pageY) —— 绝对坐标，
		window.scrollBy(x,y) —— 相对当前位置进行滚动，
		elem.scrollIntoView(top) —— 滚动以使 elem 可见（elem 与窗口的顶部/底部对齐）。




#### 坐标
移动页面的元素
	**相对于窗口**：从窗口的顶部/左侧边缘计算得出，坐标表示为 `clientX/clientY`，
	**相对于文档**：从文档的顶部/左侧边缘计算得出。 表示为 `pageX/pageY`。

页面上的任何点都有坐标：
	相对于窗口的坐标 —— elem.getBoundingClientRect()。
	相对于文档的坐标 —— elem.getBoundingClientRect() 加上当前页面滚动。
窗口坐标非常适合和 `position:fixed` 一起使用，文档坐标非常适合和 `position:absolute` 一起使用。
这两个坐标系统各有利弊。有时我们需要其中一个或另一个，就像 CSS `position` 的 `absolute` 和 `fixed` 一样。






### 事件简介

#### 浏览器事件简介

**事件** 某事发生的信号。所有的 DOM 节点都生成这样的信号（但事件不仅限于 DOM）。鼠标、键盘、表单、document事件等等
**处理程序（handler）**—— 一个在事件发生时运行的函数。
3 种分配事件处理程序的方式：
	**HTML 特性**：onclick=”....“，函数后需要()调用
	**DOM 属性** elem.onclick = function，
			只需要函数名不需要()；
			无法为特定事件分配多个程序
		- 如果一个处理程序是通过 HTML 特性（attribute）分配的，那么随后浏览器读取它，并从特性的内容创建一个新函数，并将这个函数写入 DOM 属性（property）。因此两种方法实际相同；
		- 移除一个处理程序 —— 赋值 `elem.onclick = null`。
	**方法（method）**：可以为一个事件分配多个处理程序；少数事件只能使用这种方式
		添加处理程序：
			element.addEventListener(event, handler[, options]);多次调用允许添加多个处理程序。相比dom属性更通用。event事件，handler处理程序，options的附加可选对象once，如果为 `true`，那么会在被触发后自动删除监听器。capture，事件处理的阶段。passive，如果为 `true`，那么处理程序将不会调用 `preventDefault()`。
		对象处理程序：handleEvent
			可以使用 `addEventListener` 将一个对象分配为事件处理程序。当事件发生时，就会调用该对象的 `handleEvent` 方法。即addEventListener可以接收一个对象作为处理程序，该对象设置一个handleEvent方法。
		移除处理程序 `removeEventListener`：需要传入与分配的函数完全相同的函数。
事件对象
	事件发生时，浏览器会创建一个 **`event` 对象**，将详细信息放入其中，并将其作为参数传递给处理程序。
	html特性中也可以使用event对象；
**访问元素this**，处理程序中的 `this` 的值是对应的元素。就是处理程序所在的那个元素。
**不要对处理程序使用 `setAttribute`。**DOM 属性是大小写敏感的。**






#### 冒泡和捕获
冒泡
	指一个过程：当一个事件发生在一个元素上，它会首先运行在该元素上的处理程序，然后运行其父元素上的处理程序，然后一直向上到其他祖先上的处理程序，一直到html、document或者window。
停止冒泡：任意处理程序都可以决定事件已经被完全处理，并停止冒泡。不建议用；
		event.stopPropagation()：停止某个处理程序冒泡，可作用于html特性上；但当前元素的其他处理程序会继续运行；
		event.stopImmediatePropagation()：可同时阻止当前元素的当前处理程序和其他处理程序的冒泡；
每个处理程序都可以访问 event 对象的属性：
	event.target：事件发生的实际元素、目标元素；
	`this`（=`event.currentTarget`）：当前处理程序对应的元素；
	`event.eventPhase` —— 当前阶段（capturing=1，target=2，bubbling=3）
捕获
	事件发生后，传播的 3 个阶段：
		捕获阶段—— 事件（从 Window）向下走近元素。
		目标阶段—— 事件到达目标元素。
		冒泡阶段—— 事件从元素上开始冒泡。在此途中调用处理程序；
在捕获阶段捕获事件
	设置addEventListener中的参数capture；capture ，false则在冒泡阶段设置处理程序；true，则在捕获阶段设置处理程序。
	elem.addEventListener(..., {capture: true})
要移除处理程序，removeEventListener 需要同一阶段；
同一元素的同一阶段的监听器按其设置顺序运行




#### 事件委托
事件委托模式
	通常用于为许多相似的元素添加相同的处理。
		算法：
			在容器（container）上放一个处理程序。
			在处理程序中 —— 检查源元素 event.target。
			如果事件发生在我们感兴趣的元素内，那么处理该事件。
		好处：
			简化初始化并节省内存：无需添加许多处理程序。
			更少的代码：添加或移除元素时，无需添加/移除处理程序。
			DOM 修改 ：我们可以使用 innerHTML 等，来批量添加/移除元素
事件委托局限性
	事件必须冒泡，低级别的处理程序不应该使用 `event.stopPropagation()`。
	委托可能会增加 CPU 负载，因为容器级别的处理程序会对容器中任意位置的事件做出反应，而不管我们是否对该事件感兴趣。但是，通常负载可以忽略不计，所以我们不考虑它。



#### 浏览器默认行为
许多浏览器的默认行为
	- `mousedown` —— 开始选择（移动鼠标进行选择）。
	- submit
	- keydown
	- contextmenu右击显示浏览器上下文菜单
阻止浏览器行为
	两种方式阻止浏览器默认行为
		使用`event.preventDefault()` 方法。
		return false，针对过 `on<event>` 分配的处理程序。非addEventListener；
如果默认行为被阻止，`event.defaultPrevented` 属性为 `true`，否则为 `false`。
可以使用 `event.defaultPrevented` 来代替停止冒泡event.stopPropagation()
保持HTML 元素的语义，不要滥用






#### 创建自定义事件
不仅可以分配事件处理程序，还可以从 JavaScript 生成事件。
事件构造器
	内建事件类形成一个层次结构，类似于 DOM 元素类。根是内建的 [Event](http://www.w3.org/TR/dom/#event) 类。
	创建event对象
		let event = new Event(type[, options]);     type//时间类型，options//两个可选属性的对象：bubbles，为 `true`，那么事件会冒泡；cancelable，为 `true`，那么“默认行为”就会被阻止。默认情况都为false；
内建事件（`click`）和自定义事件（`hello`）的冒泡机制相同。自定义事件也有捕获阶段和冒泡阶段。
elem.dispatchEvent(event) ：在元素上“运行”，处理程序会对它做出反应；
event.isTrusted：区分“真实”用户事件和通过脚本生成的事件，true//真实用户操作的事件；
- 其他像 `MouseEvent` 和 `KeyboardEvent` 这样的原生事件的构造器，都接受特定于该事件类型的属性。例如，鼠标事件的 `clientX`。
- 对于自定义事件，我们应该使用 `CustomEvent` 构造器。它有一个名为 `detail` 的附加选项，我们应该将事件特定的数据分配给它。然后，所有处理程序可以以 `event.detail` 的形式来访问它。
- 最好不应该生成浏览器事件，像 `click` 或 `keydown` 这样的浏览器事件。
- 可以生成原生事件：
	- 如果第三方程序库不提供其他交互方式，那么这是使第三方程序库工作所需的一种肮脏手段。
	- 对于自动化测试，要在脚本中“点击按钮”并查看接口是否正确响应。
- 使用我们自己的名称的自定义事件通常是出于架构的目的而创建的，以指示发生在菜单（menu），滑块（slider），轮播（carousel）等内部发生了什么。



### UI事件

#### 鼠标事件
与点击相关的事件始终具有 `button` 属性，该属性允许获取确切的鼠标按钮。
所有的鼠标事件都提供了两种形式的坐标：
	1. 相对于窗口的坐标：`clientX` 和 `clientY`。
	2. 相对于文档的坐标：`pageX` 和 `pageY`。
`mousedown` 的默认浏览器操作是文本选择



#### 移动鼠标：mouseover/out，mouseenter/leave
研究鼠标在元素之间移动时发生的事件。
事件 mouseover/mouseout，relatedTarget
	mouseover：鼠标移到某个元素
		event.target —— 是鼠标移过的那个元素。
		event.relatedTarget —— 是鼠标来自的那个元素（relatedTarget → target）。
	mouseout ：鼠标离开某元素
		event.target —— 是鼠标离开的元素。
		event.relatedTarget —— 是鼠标移动到的，当前指针位置下的元素（target → relatedTarget）。
	鼠标指针从元素移动到其后代时也会触发`mouseover/out` 事件。
	relatedTarget可以为null；
	如果 `mouseover` 被触发了，则必须有 `mouseout`；
	速度很快时，中间的部分元素可能会跳过；
事件 mouseenter 和 mouseleave
	类似于 `mouseover/mouseout`，在鼠标指针进入/离开元素时触发。
	区别：
		1. 元素内部与后代之间的转换不会产生影响。
		2. 事件 `mouseenter/mouseleave` 不会冒泡。
	无冒泡所以不允许事件委托。



#### 鼠标拖放事件
拖放算法
	1. 在 `mousedown` 上 —— 根据需要准备要移动的元素（也许创建一个它的副本，向其中添加一个类或其他任何东西）。
	2. 然后在 `mousemove` 上，通过更改 `position:absolute` 情况下的 `left/top` 来移动它。
	3. 在 `mouseup` 上 —— 执行与完成的拖放相关的所有行为。
	4. 不要忘记取消原生 `ondragstart`）。
	5. 在拖动开始时 —— 记住鼠标指针相对于元素的初始偏移（shift）：`shiftX/shiftY`，并在拖动过程中保持它不变。
	6. 使用 `document.elementFromPoint` 检测鼠标指针下的 “droppable” 的元素。

`document.elementFromPoint(clientX, clientY)`：返回在给定的窗口相对坐标处的嵌套的最深的元素（如果给定的坐标在窗口外，则返回 `null`）。如果同一坐标上有多个重叠的元素，则返回最上面的元素。

在此基础上做很多事情。
- 在 `mouseup` 上，我们可以智能地完成放置（drop）：更改数据，移动元素。
- 我们可以高亮我们正在“飞过”的元素。
- 我们可以将拖动限制在特定的区域或者方向。
- 我们可以对 `mousedown/up` 使用事件委托。一个大范围的用于检查 `event.target` 的事件处理程序可以管理数百个元素的拖放。
- 等。
框架：`DragZone`，`Droppable`，`Draggable` 及其他 class；




#### 指针事件
一种用于处理来自各种输入设备（例如鼠标、触控笔和触摸屏等）的输入信息的现代化解决方案。鼠标、触摸事件等等；
用 `pointer` 替换 `mouse`
事件：pointercancel
	事件将会在一个正处于活跃状态的指针交互由于某些原因被中断时触发。也就是在这个事件之后，该指针就不会继续触发更多事件了。
对于浏览器可能会决定进行劫持并自行处理的拖放和复杂的触控交互 —— 请记住取消事件的默认操作，并在 CSS 中为涉及到的元素设置 touch-action: none。

指针事件还额外具备以下能力：
	基于 pointerId 和 isPrimary 的多点触控支持。
	针对特定设备的属性，例如 pressure 和 width/height 等。
	指针捕获：我们可以把 pointerup/pointercancel 之前的所有指针事件重定向到一个特定的元素。





#### 键盘：keydown 和 keyup
键盘事件：
- `keydown` —— 在按下键时（如果长按按键，则将自动重复），
- `keyup` —— 释放按键时。
键盘事件的主要属性：
- `code` —— “按键代码”（`"KeyA"`，`"ArrowLeft"` 等），特定于键盘上按键的物理位置。
- `key` —— 字符（`"A"`，`"a"` 等），对于非字符（non-character）的按键，通常具有与 `code` 相同的值





#### 滚动
`scroll` 事件允许对页面或元素滚动作出反应。
启动滚动
	方式有很多，使用 CSS 的 `overflow` 属性更加可靠。
防止滚动
	可以在导致滚动的事件上，例如在 pageUp 和 pageDown 的 `keydown` 事件上，使用 `event.preventDefault()` 来阻止滚动。
	能通过在 `onscroll` 监听器中使用 `event.preventDefault()` 来阻止滚动，因为它会在滚动发生 **之后** 才触发。



### 表单、控件

#### 表单属性和方法
表单
	文档中的表单是特殊集合 `document.forms` 的成员。是被命名的集合，有序的’
	获取表单：
		document.forms.name，使用名字name属性
		document.forms[index]，使用文档中有序的编号
	获取表单中的子元素
		form.elements.name，form.elements[index]，通过命名的集合
		form.name，form[index]
	反向引用
		element.form，访问任意元素其所对应的表单；
表单控件
	input.value、input.checked
	textarea.value
	 `<select>`：select.options、select.value、select.selectedIndex；
		 为select设置value：设置option.selected=true；设置select.value；select.selectedIndex设为对应编号；
		 `multiple` 多选特性，用selected设置；
		创建一个option元素：
			option = new Option(text, value, defaultSelected, selected);
				text//文本，defaultSelected//为true则`selected` HTML-特性（attribute）就会被创建，selected//该option会被选中；
				**defaultSelected参数**：设置的是 HTML-特性，可以使用 `option.getAttribute('selected')` 来获得；
				**selected参数**：设置的是选项是否被选中。    实际使用中，两者应同时设为true或false；
			option元素的属性
				option.selected
				option.index
				option.text








#### 聚焦：focus/blur
聚焦————准备在此处接受数据
	元素获得聚焦
		方式：点击元素、Tab 键选中、HTML 特性`autofocus`：网页加载时聚焦某元素；
		触发 elem.focus()事件
	失去焦点
		数据已经输入完成。
		触发 elem.blur()事件。
	有些元素不支持聚焦
		html特性tabindex：任何元素具有 `tabindex` 特性都会变成可聚焦；依据其value值不同，元素焦点切换顺序也不一样；
focus/blur 委托
	`focus` 和 `blur` 事件不会向上冒泡。但会在捕获阶段向下传播
 focusin 和 focusout 事件
		与 `focus/blur` 事件完全一样，只是它们会冒泡。
		必须使用 `elem.addEventListener` 来分配它们，而不是 `on<event>`。
可以通过 `document.activeElement` 来获取当前所聚焦的元素。






#### 事件：change，input，cut，copy，paste
change 事件
	当元素更改完成时将触发
 input 事件
	 对输入值进行修改后触发
事件：cut，copy，paste
	剪切/拷贝/粘贴一个值的时候。
	属于 ClipboardEvent 类，提供了对剪切/拷贝/粘贴的数据的访问方法。
	可以使用 `event.preventDefault()` 来中止，根本不会被复制。
	调用 `event.clipboardData.getData(...)`，在剪切/复制事件处理程序中调用只会得到一个空字符串。
安全限制
	剪贴板是“全局”操作系统级别的东西。存在不同应用程序间操作。
	除火狐（Firefox）浏览器外，所有浏览器都禁止使用 `dispatchEvent` 生成“自定义”剪贴板事件。合成（syntetic）事件不得提供对剪切板的访问权限。event.clipboardData 属性可以用于访问剪贴板。除了火狐（Firefox）之外的浏览器都支持navigator.clipboard。
	event.clipboardData 仅在用户启动的事件处理程序的上下文中生效。
	navigator.clipboard 是一个较新的 API，适用于任何上下文。如果需要，它会请求用户的许可。






#### 表单：事件和方法提交
 submit 事件
	 它通常用于在将表单发送到服务器之前对表单进行校验，或者中止提交，并使用 JavaScript 来处理表单。
	 form.submit() ，可从 JavaScript 启动表单发送，可以动态地创建表单，并将其发送到服务器。
	可以使用 event.preventDefault()，阻止行为；
	 提交表单的两种方式
		 点击 `<input type="submit">` 或 `<input type="image">`。
		 在 `input` 字段中按下 Enter 键。
	手动将表单提交到服务器
		调用 `form.submit()`，且不会产生submit事件，可用来手动创建和发送表单。






### 加载文档和其他资源

#### 页面生命周期：DOMContentLoaded，load，beforeunload，unload
HTML 页面的生命周期包含三个重要事件
	DOMContentLoaded事件，
			- 浏览器已完全加载 HTML，并构建了 DOM 树，但外部资源可能尚未加载完成。处理程序可以查找DOM节点，并初始化接口
			- 在 `document` 对象上，需使用addEventListener捕获；
			- 浏览器处理html文档时，遇到script标签会加载脚本后再继续构建DOM，然后发生DOMContentLoaded事件。除非（有`async` 特性的脚本或者document.createElement('script'）动态添加脚本不会干扰）。
			- 外部样式不会影响 DOM。除非样式表后面有一个脚本 script标签，需等加载完样式表再脚本再DOMContentLoaded事件。
			- 浏览器会在DOMContentLoaded事件中自动填充表单。
	load事件，
			浏览器不仅加载完成了 HTML，还加载完成了所有外部资源：图片，样式等。会触发window对象的load事件；可用window的onload属性获取该事件；
	beforeunload/unload事件 
			当用户正在离开页面时。可检查用户是否保存更改等；
			用户想要离开页面时，会触发beforeunload事件，若取消该事件，则会询问是否真的离开。
		unload事件：
			用户最终离开时可执行一些操作、如发送统计数据；
			离开页面时触发window对象的unload事件；
			navigator.sendBeacon(url, data)方法，收集页面的相关数据并发送到服务器；
			`keep-alive` 标志，
document.readyState 属性
	提供文档当前加载状态的信息。
	值
		loading —— 文档正在被加载。
		interactive —— 文档被全部读取。
		complete —— 文档被全部读取，并且所有资源（例如图片等）都已加载完成。
	可为readyState设置处理程序。
readystatechange事件
	跟踪文档加载状态
`document.readyState` 是文档的当前状态，可以在 `readystatechange` 事件中跟踪状态更改：
	- `loading` —— 文档正在被加载。
	- `interactive` —— 文档已被解析完成，与 `DOMContentLoaded` 几乎同时发生，但是在 `DOMContentLoaded` 之前发生。
	- `complete` —— 文档和资源均已加载完成，与 `window.onload` 几乎同时发生，但是在 `window.onload` 之前发生。







#### 脚本：async，defer
浏览器加载html时先执行遇到的script标签再构建DOM，浏览器需先等遇到的外部script脚本下载完再继续处理剩余页面；
	存在的问题
		脚本无法访问下方的DOM元素
		上方复杂的脚本易阻塞页面
defer特性
	defer特性的脚本会在后台下载，不会阻塞页面，dom的构建。
	要等到 DOM 解析完毕，但在 `DOMContentLoaded` 事件之前执行。
	具有 defer 特性的脚本执行时保持其相对顺序，就像常规脚本一样。
	`defer` 特性仅适用于外部脚本。
	用于需要整个 DOM 的脚本，和/或脚本的相对执行顺序很重要的时候。
async特性
	一个会在加载完成时执行的完全独立的脚本。
	async脚本会在后台加载，且加载就绪时运行，与dom和其他脚本不会互相等待。先加载完成的先执行；
	`DOMContentLoaded` 和异步脚本也不会互相等待。
	可在独立的第三方脚本集成到页面时应用；
	`async` 特性仅适用于外部脚本。
	用于独立脚本，例如计数器或广告，这些脚本的相对执行顺序无关紧要。
动态脚本
	使用 JavaScript 动态地创建一个脚本，并附加到文档中。
	是异步的，不会等待，先加载完成的先执行；

如果你使用的是 `defer` 或 `async`，那么用户将在脚本加载完成 **之前** 先看到页面。
在这种情况下，某些图形组件可能尚未初始化完成。需进行提示处理；







#### 资源加载：onload，onerror
图片 `<img>`，外部样式，脚本和其他资源都提供了 `load` 和 `error` 事件以跟踪它们的加载，仅跟踪加载本身；
- `load` 在成功加载时被触发。script.onload。即使脚本成功加载，但有error也会触发load；
- `error` 在加载失败时被触发。script.onerror。跟踪脚本 error，可以`window.onerror` 全局处理程序。
`load` 和 `error` 事件
	基本上适用于具有外部src的外部资源。
	但大多数资源被添加到文档中便开始加载，但img要等到获得 src `(*)` 后才开始加载。
	对于 `<iframe>` 来说，iframe 加载完成时会触发 `iframe.onload` 事件，无论是成功加载还是出现 error。

跨源策略
	来自一个网站的脚本无法访问其他网站的内容。
	有关脚本内部的任何信息（包括 error 堆栈跟踪）都被隐藏了。正是因为它来自于另一个域。

需要 error 的详细信息的原因
	因为有很多服务使用 `window.onerror` 监听全局 error，保存 error 并提供访问和分析 error 的接口。这很好，因为我们可以看到由用户触发的实际中的 error。
其他类型的资源也执行类似的跨源策略（CORS）
	**要允许跨源访问，`<script>` 标签需要具有 `crossorigin` 特性（attribute），并且远程服务器必须提供特殊的 header。**

有三个级别的跨源访问：
1. **无 `crossorigin` 特性** —— 禁止访问。
2. **`crossorigin="anonymous"`** —— 如果服务器的响应带有包含 `*` 或我们的源（origin）的 header `Access-Control-Allow-Origin`，则允许访问。浏览器不会将授权信息和 cookie 发送到远程服务器。
3. **`crossorigin="use-credentials"`** —— 如果服务器发送回带有我们的源的 header `Access-Control-Allow-Origin` 和 `Access-Control-Allow-Credentials: true`，则允许访问。浏览器会将授权信息和 cookie 发送到远程服务器。
`readystatechange` 事件也适用于资源，但很少被使用，因为 `load/error` 事件更简单。





### 杂项

#### DOM 变动观察器（Mutation observer）
MutationObserver内建对象
	观察 DOM 元素，并在检测到更改时触发回调。
	创建一个带有回调函数的观察器：
```javascript
let observer = new MutationObserver(callback);
observer.observe(node, config);
```
config对象：具有布尔选项
	- `childList` —— `node` 的直接子节点的更改，
	- `subtree` —— `node` 的所有后代的更改，
	- `attributes` —— `node` 的特性（attribute），
	- `attributeFilter` —— 特性名称数组，只观察选定的特性。
	- `characterData` —— 是否观察 `node.data`（文本内容）
	- `attributeOldValue` —— 如果为 `true`，则将特性的旧值和新值都传递给回调，否则只传新值（需要 `attributes` 选项），
	- `characterDataOldValue` —— 如果为 `true`，则将 `node.data` 的旧值和新值都传递给回调，否则只传新值（需要 `characterData` 选项）。
发生更改后将执行回调，更改被作为一个 MutationRecord 对象列表传入第一个参数，而观察器自身作为第二个参数。
MutationRecord 对象属性
	type —— 变动类型，以下类型之一：
		"attributes"：特性被修改了，
		"characterData"：数据被修改了，用于文本节点，
		"childList"：添加/删除了子元素。
	target —— 更改发生在何处："attributes" 所在的元素，或 "characterData" 所在的文本节点，或 "childList" 变动所在的元素，
	addedNodes/removedNodes —— 添加/删除的节点，
	previousSibling/nextSibling —— 添加/删除的节点的上一个/下一个兄弟节点，
	attributeName/attributeNamespace —— 被更改的特性的名称/命名空间（用于 XML），
	oldValue —— 之前的值，仅适用于特性或文本更改，如果设置了相应选项 attributeOldValue/characterDataOldValue。

使用场景
	第三方脚本，该脚本不仅包含有用的功能，还会执行一些我们不想要的操作时。可以监控不需要的元素和内容的出现；

停止观察节点：
	observer.disconnect() —— 停止观察。
	对于已停止观察但观察器尚未处理某些更改时，observer.takeRecords() —— 获取尚未处理的变动记录列表，表中记录的是已经发生，但回调暂未处理的变动。
	observer.takeRecords() 返回的记录被从处理队列中移除。
垃圾回收
	观察器在内部对节点使用弱引用。也就是说，如果一个节点被从 DOM 中移除了，并且该节点变得不可访问，那么它就可以被垃圾回收。观察到 DOM 节点这一事实并不能阻止垃圾回收。









#### 选择（Selection）和范围（Range）
Range
	本质上是一对“边界点”：范围起点和范围终点。
	let range = new Range();
	使用 range.setStart(node, offset) 和 range.setEnd(node, offset) 来设置选择边界。
	选择部分文本
		**`node` 是一个文本节点，那么 `offset` 则必须是其文本中的位置。**
	选择元素节点
		**如果 `node` 是一个元素节点，那么 `offset` 则必须是子元素的编号。**
	range 属性
		startContainer，startOffset —— 起始节点和偏移量，
		endContainer，endOffset —— 结束节点和偏移量，
		collapsed —— 布尔值，如果范围在同一点上开始和结束（所以范围内没有内容）则为 true，
		commonAncestorContainer —— 在范围内的所有节点中最近的共同祖先节点，
	其他选择范围的方法（除setStart 和 setEnd）
		设置范围的起点：
				setStart(node, offset) 将起点设置在：node 中的位置 offset
				setStartBefore(node) 将起点设置在：node 前面
				setStartAfter(node) 将起点设置在：node 后面
		设置范围的终点（类似的方法）：
				setEnd(node, offset) 将终点设置为：node 中的位置 offset
				setEndBefore(node) 将终点设置为：node 前面
				setEndAfter(node) 将终点设置为：node 后面
		node 都可以是文本或者元素节点：对于文本节点，偏移量 offset 跨越的是很多字母，而对于元素节点则跨越的是很多子节点。
		更多创建范围的方法：
				selectNode(node) 设置范围以选择整个 node
				selectNodeContents(node) 设置范围以选择整个 node 的内容
				collapse(toStart) 如果 toStart=true 则设置 end=start，否则设置 start=end，从而折叠范围
				cloneRange() 创建一个具有相同起点/终点的新范围
		编辑范围的方法
				deleteContents() —— 从文档中删除范围中的内容
				extractContents() —— 从文档中删除范围中的内容，并将删除的内容作为 DocumentFragment 返回
				cloneContents() —— 复制范围中的内容，并将复制的内容作为 DocumentFragment 返回
				insertNode(node) —— 在范围的起始处将 node 插入文档
				surroundContents(node) —— 使用 node 将所选范围中的内容包裹起来。要使此操作有效，则该范围必须包含其中所有元素的开始和结束标签：不能像 `<i>abc` 这样的部分范围。
	Range
		是用于管理选择范围的通用对象；
selection
	文档选择是由 Selection 对象表示的，可通过 window.getSelection() 或 document.getSelection() 来获取。一个选择可以包括零个或多个范围。
	选择属性
		getRangeAt(i) —— 获取第 i 个范围，i 从 0 开始。
		与范围类似，选择的起点被称为“锚点（anchor）”，终点被称为“焦点（focus）”。
		anchorNode —— 选择的起始节点，
		anchorOffset —— 选择开始的 anchorNode 中的偏移量，
		focusNode —— 选择的结束节点，
		focusOffset —— 选择开始处 focusNode 的偏移量，
		isCollapsed —— 如果未选择任何内容（空范围）或不存在，则为 true 。
		rangeCount —— 选择中的范围数，除 Firefox 外，其他浏览器最多为 1。
selection和range的起点和终点对比
	Range 对象的起点必须在其终点之前。
	选择的终点可以在起点之前，如鼠标选择；
selection事件
	有一些事件可以跟踪选择
	elem.onselectstart —— 当在元素 elem 上（或在其内部）开始选择时。
	document.onselectionchange —— 当选择发生变化或开始时。
选择复制
	复制所选内容有两种方式：
		document.getSelection().toString() 来获取其文本形式。
		复制整个 DOM 节点,使用 getRangeAt(...) 获取底层的（underlying）范围。
		Range 对象还具有 cloneContents() 方法，该方法会拷贝范围中的内容并以 DocumentFragment 的形式返回，我们可以将这个返回值插入到其他位置。
选择方法
	通过添加/移除范围来处理选择：
		getRangeAt(i) —— 获取从 0 开始的第 i 个范围。在除 Firefox 之外的所有浏览器中，仅使用 0。
		addRange(range) —— 将 range 添加到选择中。如果选择已有关联的范围，则除 Firefox 外的所有浏览器都将忽略该调用。
		removeRange(range) —— 从选择中删除 range。
		removeAllRanges() —— 删除所有范围。
		empty() —— removeAllRanges 的别名。
	还有一些方便的方法可以直接操作选择范围，而无需中间的 Range 调用：
		collapse(node, offset) —— 用一个新的范围替换选定的范围，该新范围从给定的 node 处开始，到偏移 offset 处结束。
		setPosition(node, offset) —— collapse 的别名。
		collapseToStart() —— 折叠（替换为空范围）到选择起点，
		collapseToEnd() —— 折叠到选择终点，
		extend(node, offset) —— 将选择的焦点（focus）移到给定的 node，位置偏移 offset，
		setBaseAndExtent(anchorNode, anchorOffset, focusNode, focusOffset) —— 用给定的起点 anchorNode/anchorOffset 和终点 focusNode/focusOffset 来替换选择范围。选中它们之间的所有内容。
		selectAllChildren(node) —— 选择 node 的所有子节点。
		deleteFromDocument() —— 从文档中删除所选择的内容。
		containsNode(node, allowPartialContainment = false) —— 检查选择中是否包含 node（若第二个参数是 true，则只需包含 node 的部分内容即可）
		对于大多数需求，这些方法就够了，无需访问底层的（underlying）Range 对象。
如要选择一些内容，请先移除现有的选择：使用 removeAllRanges() 将其清空。然后添加范围。

表单控件中的选择
	如 input 和 textarea 等表单元素提供了专用的选择api。没有 `Selection` 或 `Range` 对象。由于输入值是纯文本而不是 HTML，因此不需要此类对象。
	属性
		input.selectionStart —— 选择的起始位置（可写），
		input.selectionEnd —— 选择的结束位置（可写），
		input.selectionDirection —— 选择方向，其中之一：“forward”，“backward” 或 “none”（例如使用鼠标双击进行的选择），
	事件
		input.onselect —— 当某个东西被选择时触发。
	方法
		input.select() —— 选择文本控件中的所有内容（可以是 textarea 而不是 input），
		input.setSelectionRange(start, end, [direction]) —— 在给定方向上（可选），从 start 一直选择到 end。
		input.setRangeText(replacement, [start], [end], [selectionMode]) —— 用新文本替换范围中的文本。
		选参数 start 和 end，如果提供的话，则设置范围的起点和终点，否则使用用户的选择。
		最后一个参数 selectionMode 决定替换文本后如何设置选择。可能的值为：
			"select" —— 将选择新插入的文本。
			"start" —— 选择范围将在插入的文本之前折叠（光标将在其之前）。
			"end" —— 选择范围将在插入的文本之后折叠（光标将紧随其后）。
			"preserve" —— 尝试保留选择。这是默认值。

使不可选
	要使某些内容不可选，有三种方式：
		使用 CSS 属性 user-select: none。
		防止 onselectstart 或 mousedown 事件中的默认行为。
		使用 document.getSelection().empty() 来在选择发生后清除选择。很少使用这种方法，因为这会在选择项消失时导致不必要的闪烁。
关于光标。在诸如 `<textarea> `之类的可编辑元素中，光标的位置始终位于选择的起点或终点。我们可以通过设置 elem.selectionStart 和 elem.selectionEnd 来获取光标位置或移动光标。






#### 事件循环：微任务和宏任务

浏览器中的js和nodejs中的执行流程都是基于事件循环的；
理解事件循环的对于代码优化和架构很重要；

事件循环
	是一个在js引擎中等待任务、执行任务、进入休眠状态等待更多任务之间转换的的无限循环。
	宏队列中执行任务；
	执行微任务
	有变更则渲染
	休眠直到新宏任务；
引擎
	引擎的一般算法：有任务时，开始执行最先的任务。休眠。再反复。
	引擎大多数时候不执行操作。仅在脚本/处理程序/事件激活时执行。
	**宏任务队列**：引擎繁忙时众多需要处理的任务组成的队列。先进先出；
	引擎执行任务时永远不会进行渲染，完成后才会更改dom；
	抛出页面未响应警报：由于大量复杂的计算或导致死循环的程序错误时，任务时间长而无法执行其他任务；
	应用
		将大任务拆分成小任务；
		显示进度指示；
		某些事件的推迟处理；

宏任务和微任务
	微任务：
		微任务仅来自于我们的代码；
		通常是由 promise 创建的：对 `.then/catch/finally` 处理程序的执行会成为微任务。微任务也被用于 `await` 的“幕后”，因为它是 promise 处理的另一种形式。
		还有一个特殊的函数 `queueMicrotask(func)`，它对 `func` 进行排队，以在微任务队列中执行。
		微任务会在执行任何其他事件处理，或渲染，或执行任何其他宏任务之前完成。确保了微任务之间的应用程序环境基本相同（没有鼠标坐标更改，没有新的网络数据等）。
		queueMicrotask：在更改被渲染或新事件被处理之前，异步执行一个函数；
		微任务之间没有 UI 或网络事件的处理：它们一个立即接一个地执行。所以，我们可以使用 `queueMicrotask` 来在保持环境状态一致的情况下，异步地执行一个函数。
	每个宏任务之后，引擎会立即执行微任务队列中的所有任务，然后再执行其他的宏任务，或渲染，或进行其他任何操作。
		安排一个新的 宏任务：使用零延迟的 setTimeout(f)。
Web Workers
	对于不应该阻塞事件循环的耗时长的繁重计算任务，我们可以使用 Web Workers。——在另一个并行线程中运行代码的方式。





### Frame 和 window

#### 弹窗和 window 的方法
概述
	弹窗
		一般地打开：window.open('https://javascript.info/')
		打开具有新url的窗口（比较少用），一般都在新选项卡中打开url；弹窗很少使用，因为有其他选择：在页面内或在 iframe 中加载和显示信息。
		浏览器一般会阻止弹窗保护用户，如用户触发的处理程序之外调用的弹窗；
		语法：          window.open(url, name, params)：
			name：新窗口的名称，window.name
			params：新窗口的配置字符串。它包括设置，用逗号分隔。参数之间不能有空格。params 的设置项：
				位置:
					left/top（数字）—— 屏幕上窗口的左上角的坐标。这有一个限制：不能将新窗口置于屏幕外（offscreen）。
					width/height（数字）—— 新窗口的宽度和高度。宽度/高度的最小值是有限制的，因此不可能创建一个不可见的窗口。
				窗口功能：
					menubar（yes/no）—— 显示或隐藏新窗口的浏览器菜单。
					toolbar（yes/no）—— 显示或隐藏新窗口的浏览器导航栏（后退，前进，重新加载等）。
					location（yes/no）—— 显示或隐藏新窗口的 URL 字段。Firefox 和 IE 浏览器不允许默认隐藏它。
					status（yes/no）—— 显示或隐藏状态栏。同样，大多数浏览器都强制显示它。
					resizable（yes/no）—— 允许禁用新窗口大小调整。不建议使用。
					scrollbars（yes/no）—— 允许禁用新窗口的滚动条。不建议使用。
		设置中的省略规则：
			如果 open 调用中没有第三个参数，或者它是空的，则使用默认的窗口参数。
			如果这里有一个参数字符串，但是某些 yes/no 功能被省略了，那么被省略的功能则被默认值为 no。因此，如果你指定参数，请确保将所有必需的功能明确设置为 yes。
			如果参数中没有 left/top，那么浏览器会尝试在最后打开的窗口附近打开一个新窗口。
			如果没有 width/height，那么新窗口的大小将与上次打开的窗口大小相同。
	从窗口访问弹窗
		window.open会返回对新窗口的引用；可以用来操纵弹窗的属性，更改位置等；
		遵循同源策略，仅同源时，窗口可以互相访问内容
	从弹窗访问窗口
		弹窗通过window.opener访问opener 窗口；
	窗口之间的连接是双向的：主窗口和弹窗之间相互引用。
	关闭弹窗：win.close()。close()只对弹窗有用；
	检查窗口是否被关闭：win.closed。
	窗口的移动和调整大小
		win.moveBy(x,y)，将窗口相对于当前位置向右移动 `x` 像素，并向下移动 `y` 像素。允许负值
		win.moveTo(x,y)，将窗口移动到屏幕上的坐标 `(x,y)` 处。
		win.resizeBy(width,height)，根据给定的相对于当前大小的 `width/height` 调整窗口大小。允许负值。
		win.resizeTo(width,height)，将窗口调整为给定的大小。
		window.onresize 事件
		没有最小化/最大化
	滚动窗口
		win.scrollBy(x,y)，相对于当前位置，将窗口向右滚动 x 像素，并向下滚动 y 像素。允许负值。
		win.scrollTo(x,y)，将窗口滚动到给定坐标 (x,y)。
		elem.scrollIntoView(top = true)，滚动窗口，使 elem 显示在 elem.scrollIntoView(false) 的顶部（默认）或底部。
		window.onscroll 事件。
	弹窗的聚焦/失焦
		focus() 和 blur() 方法允许聚焦/失焦于窗口。但它们并不是一直都有效。浏览器会做限制；
		focus和 blur 事件允许跟踪窗口的切换。但是请注意，在 blur 之后，即使窗口在背景状态下，窗口仍有可能是可见的。
		应用
			打开一个弹窗时，在它上面执行 newWindow.focus() ，确保用户现在位于新窗口中。
			通过window.onfocus/onblur，跟踪访问者何时在实际使用我们的 Web 应用程序






#### 跨窗口通信
“同源”策略规定：
	窗口（如window.open弹窗或一个窗口中的iframe）若同源，则具有对该窗口的全部访问权限。
	不是同源，无法访问该窗口中的内容，例外，`location`：我们可以修改它（进而重定向用户）。但是我们无法读取 `location`

iframe
	 `<iframe>` 标签承载了一个单独的嵌入的窗口，它具有自己的 `document` 和 `window`。
	 访问
		`iframe.contentWindow` 来获取 `<iframe>` 中的 window。
		`iframe.contentDocument` 来获取 `<iframe>` 中的 document，是 `iframe.contentWindow.document` 的简写形式。
		允许的非同源iframe的访问
			iframe.contentWindow的获取
			对 `location` 进行写入
			 向其发送一条消息。
	iframe.onload与iframe.contentWindow.onload
		两者基本相同，当嵌入的窗口的全部资源加载完成触发；
		无法使用contentWindow.onload访问不同源的iframe，则使用前者；

子域上的 window：document.domain————已弃用，但有效
	不同源但二级域相同的窗口，可以当做同源对待，以进行跨窗口通信；且每个窗口执行代码：document.domain = 'site.com';
	document.domain正被规范删除

Iframe：错误文档陷阱
	不能在iframe文档未加载完成时进行处理。当iframe中文档未完成加载时，与最终加载完成的文档不一样。
	应在整个 iframe和资源都加载完成后即触发iframe.onload时，才可操作；可通过setInterval检查完成时刻；

对于iframe访问父/子窗口
	window.frames —— 一个嵌套的 window 对象的集合，window.iframes[index]、window.frames.iframeName
	window.parent，window.top 是对父窗口和顶级窗口的引用，（多级iframe嵌套）
	iframe.contentWindow 是 `<iframe>` 标签内的 window 对象。

“sandbox” iframe 特性
	如果一个 iframe 具有 sandbox 特性，则它会被强制处于“非同源”状态，除非在其特性值中指定了 allow-same-origin。这可用于在同一网站的 iframe 中运行不受信任的代码
	allow-top-navigation，允许 iframe 更改 parent.location。
	allow-forms，允许在 iframe 中提交表单。
	allow-scripts，允许在 iframe 中运行脚本。
	allow-popups，允许在 iframe 中使用 window.open 打开弹窗。
	"sandbox" 特性的目的仅是 添加更多 限制。它无法移除这些限制，如果 iframe 来自其他源，则无法放宽同源策略。

跨窗口通信
	postMessage 接口允许两个具有任何源的窗口之间进行通信，双方均调用相同的js函数；接口有两部分
	postMessage
		发送窗口调用接收窗口的 postMessage 方法；win.postMessage(data, targetOrigin)
			data：发送数据，可以是任何对象。数据会被通过使用结构化序列化算法克隆。
			targetOrigin：目标窗口的源。可为* 值，否则是为了检查目标源是否正确；
	onmessage
		当postMessage函数调用时，触发目标窗口的message事件，且调用对应处理程序
		该event对象具有特殊属性：
			data：从 postMessage 传递来的数据。
			origin：发送方的源。
			source：对发送方窗口的引用，
		处理程序：使用 addEventListener。





#### 点击劫持攻击
“点击劫持”攻击允许恶意页面 **以用户的名义** 点击“受害网站”。
原理：
	在恶意页面上放置一个iframe。内部放置受害网站。
	点击劫持是对点击事件，而非键盘事件。
传统防御
	一段用于禁止在 frame 中打开页面的 JavaScript 代码（所谓的 “framebusting”）。
	如果 window 发现它不在顶部，那么它将自动使其自身位于顶部。
阻止顶级导航
	当 iframe 试图更改 top.location 时，访问者会收到一条消息，询问他们是否要离开页面。
Sandbox 特性
	sandbox 特性的限制之一就是导航。沙箱化的 iframe 不能更改 top.location。
	可以添加具有 sandbox="allow-scripts allow-forms" 的 iframe。从而放开限制，允许脚本和表单。但我们没添加 allow-top-navigation，因此更改 top.location 是被禁止的。
X-Frame-Options
	服务器端 header X-Frame-Options 可以允许或禁止在 frame 中显示页面。
	它必须被完全作为 HTTP-header 发送：如果浏览器在 HTML `<meta>` 标签中找到它，则会忽略它。因此，`<meta http-equiv="X-Frame-Options"...>` 没有任何作用。
	header值
		DENY，始终禁止在 frame 中显示此页面。
		SAMEORIGIN，允许在和父文档同源的 frame 中显示此页面。
		ALLOW-FROM domain，允许在来自给定域的父文档的 frame 中显示此页面。
	副作用
		其他的网站即使有充分的理由也无法在 frame 中显示我们的页面。但如果我们希望允许在 frame 中显示我们的页面，那我们使用一个 `<div> `对整个页面进行遮盖，这样也是安全的。
Samesite cookie 特性
	samesite cookie 特性也可以阻止点击劫持攻击。具有 `samesite` 特性的 cookie 仅在网站是通过直接方式打开（而不是通过 frame 或其他方式）的情况下才发送到网站






### 二进制数据，文件
使用 JavaScript 处理二进制数据和文件。

#### ArrayBuffer，二进制数组
js中的二进制数据是以非标准方式实现的。
js中的二进制格式数据：ArrayBuffer，Uint8Array，DataView，Blob，File 及其他。
ArrayBufferView 是所有这些视图的总称。
BufferSource 是 ArrayBuffer 或 ArrayBufferView 的总称。

ArrayBuffer 对象
	是一个内存区域，对固定长度的连续内存空间的引用。
	是基本的二进制核心对象、原始的二进制数据，通过视图对象访问；
	创建方式：
			let buffer = new ArrayBuffer(16); 
			创建一个长度为 16 的 buffer，分配一个 16 字节的连续内存空间，并用 0 进行预填充。
	访问
		通过“视图”对象，任意TypedArray
			Uint8Array（将ArrayBuffer中的每个字节视为 0 到 255 之间的单个数字。），Uint16Array，Uint32Array —— 用于 8 位、16 位和 32 位无符号整数。
			Uint8ClampedArray —— 用于 8 位整数，在赋值时便“固定”其值。
			Int8Array，Int16Array，Int32Array —— 用于有符号整数（可以为负数）。
			Float32Array，Float64Array —— 用于 32 位和 64 位的有符号浮点数。
			应用
			let view = new Uint32Array(buffer); //将16字节空间划分为4个4字节长度整数   view[0] = 123456;//写入值
		或 DataView —— 使用方法来指定格式的视图，例如，getUint8(offset)。

类型化数组的构造器
	new TypedArray(buffer, [byteOffset], [length]);   若ArrayBuffer，根据起始位置，涵盖 `buffer` 的一部分。
	new TypedArray(object);   若数组或类数组对象，创建一个相同长度的类型化数组，并复制其内容。
	new TypedArray(typedArray);创建一个相同长度的类型化数组，并复制其内容。有可能数据在此过程中会被转换为新的类型。
	new TypedArray(length);  创建类型化数组以包含这么多元素。
	new TypedArray();  创建长度为零的类型化数组。
可不提及 ArrayBuffer直接创建一个TypedArray，但视图离不开底层的Arraybuffer，
访问底层ArrayBuffer的typeArray属性
	arr.buffer —— 引用 ArrayBuffer。
	arr.byteLength —— ArrayBuffer 的长度。
可以从一个视图转到另一个视图

越界行为
	越界值写入类型化数组，不会报错。但是多余的位被切除。

TypedArray 方法
	具有常规的 `Array` 方法
	可以遍历（iterate），map，slice，find 和 reduce 等。
	没有 splice —— 我们无法“删除”一个值，因为类型化数组是缓冲区（buffer）上的视图，并且缓冲区（buffer）是固定的、连续的内存区域。我们所能做的就是分配一个零值。
	无 concat 方法。
	arr.set(fromArr, [offset]) 从 offset（默认为 0）开始，将 fromArr 中的所有元素复制到 arr。
	arr.subarray([begin, end]) 创建一个从 begin 到 end（不包括）相同类型的新视图。这类似于 slice 方法（同样也支持），但不复制任何内容 —— 只是创建一个新视图，以对给定片段的数据进行操作。




#### TextDecoder 和 TextEncoder
当二进制数据是字符串，如包含文本数据的文件。
内建的 TextDecoder 对象
	给定缓冲区（buffer）和编码格式（encoding）的情况下，允许将值读取为实际的 JavaScript 字符串。
	创建
		let decoder = new TextDecoder([label], [options]);
			label —— 编码格式，默认为 utf-8，但同时也支持 big5，windows-1251 等许多其他编码格式。
			options —— 可选对象：
				fatal —— 布尔值，如果为 true 则为无效（不可解码）字符抛出异常，否则（默认）用字符 \uFFFD 替换无效字符。
				ignoreBOM —— 布尔值，如果为 true 则忽略 BOM（可选的字节顺序 Unicode 标记），很少需要使用。
	解码
		let str = decoder.decode([input], [options]);
		input —— 要被解码的 BufferSource。
		options —— 可选对象：
			stream —— 对于解码流，为 true，则将传入的数据块（chunk）作为参数重复调用 decoder。在这种情况下，多字节的字符可能偶尔会在块与块之间被分割。这个选项告诉 TextDecoder 记住“未完成”的字符，并在下一个数据块来的时候进行解码。
	eg. new TextDecoder().decode(uint8Array)；

TextEncoder
	将字符串转换为字节。
	let encoder = new TextEncoder();
	只支持 `utf-8` 编码。
	有两种方法：
		encode(str) —— 从字符串返回 Uint8Array。
		encodeInto(str, destination) —— 将 str 编码到 destination 中，该目标必须为 Uint8Array。







#### Blob
概述
二进制格式数据，表示“具有类型的二进制数据”。其他 `BufferSource` 是“二进制数据”
Blob 由一个可选的字符串 type（通常是 MIME 类型）和 blobParts 组成 —— 一系列其他 Blob 对象，字符串和 BufferSource。
	MIME类型（常见的text，img，audio，video）
构造函数的语法为：
	new Blob(blobParts, options);
		blobParts 是 Blob/BufferSource/String 类型的值的数组。
		options 可选对象：
			type —— Blob 类型，通常是 MIME 类型，例如 image/png，
			endings —— 是否转换换行符，使 Blob 对应于当前操作系统的换行符（\r\n 或 \n）。默认为 "transparent"（啥也不做），不过也可以是 "native"（转换）。
		let blob = new Blob(["<html>…</html>"], {type: 'text/html'});      //第一个参数必须是一个数组.
方法
	blob.slice([byteStart], [byteEnd], [contentType]);     提取 Blob 片段
		byteStart —— 起始字节，默认为 0。
		byteEnd —— 最后一个字节（不包括，默认为最后）。
		contentType —— 新 blob 的 type，默认与源 blob 相同。
Blob 对象是不可改变的，无法直接在 Blob 中更改数据。

应用
Blob 用作 URL
	Blob 可以很容易用作 `<a>`、`<img>` 或其他标签的 URL，来显示它们的内容。
	通过type可自由的可以下载/上传 `Blob` 对象。
	例：
		通过点击可下载一个具有动态生成的内容为 XXXXXX 的 `Blob` 的文件。
		URL.createObjectURL(blob)取一个 `Blob`，并为其创建一个唯一的 URL，形式为 `blob:<origin>/<uuid>`。
		浏览器内部为每个通过 `URL.createObjectURL` 生成的 URL 存储了一个 URL → `Blob` 映射。因此，此类 URL 很短，但可以访问 `Blob`。
		**因此，如果我们创建一个 URL，那么即使我们不再需要该 `Blob` 了，它也会被挂在内存中。**
	URL.revokeObjectURL(url)
		从内部映射中移除引用，因此允许 Blob 被删除（如果没有其他引用的话），并释放内存。
两种从 Blob 创建 URL 的方法
	URL.createObjectURL(blob)：更简单快捷。如果介意内存，我们需要撤销（revoke)，它们直接访问 `Blob`，无需“编码/解码”
	Blob 转换为 data url：无需撤销（revoke）任何操作。对大的 `Blob` 进行编码时，性能和内存会有损耗。
Blob 转换为 base64。
	`URL.createObjectURL` 的一个替代方法是，将 `Blob` 转换为 base64-编码的字符串。
	这种编码将二进制数据表示为一个由 0 到 64 的 ASCII 码组成的字符串，非常安全且“可读“。更重要的是 —— 我们可以在 “data-url” 中使用此编码。

Image 转换为 blob
	可以创建一个图像的、图像一部分的、一个页面截图的blob；方便将其上传至其他地方。
	图像操作是通过 `<canvas>` 元素来实现的：
		使用 canvas.drawImage 在 canvas 上绘制图像（或图像的一部分）。
		调用 canvas 方法 .toBlob(callback, format, quality) 创建一个 Blob，并在创建完成后使用其运行 callback。
	页面截屏：可以使用诸如 https://github.com/niklasvh/html2canvas 之类的库。
Blob 转换为 ArrayBuffer
	Blob 构造器允许从几乎任何东西创建 blob，包括任何 BufferSource。
	需要执行低级别的处理时，可以从 blob.arrayBuffer() 中获取最低级别的 ArrayBuffer：
Blob 转换为 Stream
	处理大型blob时，读取和写入超过 2 GB 的 blob 时，将其转换为 arrayBuffer 的使用对我们来说会更加占用内存。这种情况下，我们可以直接将 blob 转换为 stream 进行处理。
	stream
		特殊对象，可以从它逐部分地读取（或写入）。适合逐段处理的数据
	blob.stream()：Blob 接口里的 stream() 方法返回一个 ReadableStream，在被读取时可以返回 Blob 中包含的数据。





#### File 和 FileReader
File 对象
	继承自 Blob，并扩展了与文件系统相关的功能。
	两种方式获取
		与 `Blob` 类似，构造器
			new File(fileParts, fileName, [options])
				fileParts —— Blob/BufferSource/String 类型值的数组。
				fileName —— 文件名字符串。
				options —— 可选对象：
					lastModified —— 最后一次修改的时间戳（整数日期）
		从 `<input type="file">` 或拖放或其他浏览器接口来获取文件。file 将从操作系统（OS）获得 this 信息，`input.files` 是一个类数组对象。
	file对象属性
		name —— 文件名，
		lastModified —— 最后一次修改的时间戳。
如果我们要通过网络发送一个 File，那也很容易：像 XMLHttpRequest 或 fetch 等网络 API 本身就接受 File 对象。

FileReader对象
	唯一目的是从 `Blob`（因此也从 `File`）对象中读取数据。
	使用事件来传递数据，因为从磁盘读取数据可能比较费时间。
	构造函数
		let reader = new FileReader(); // 没有参数
	主要方法
		readAsArrayBuffer(blob) —— 将数据读取为二进制格式的 ArrayBuffer。用于二进制文件，执行低级别的二进制操作
		readAsText(blob, [encoding]) —— 将数据读取为给定编码（默认 utf-8 编码）的文本字符串。用于文本文件，当想要获取字符串时。
		readAsDataURL(blob) —— 读取二进制数据，并将其编码为 base64 的 data url。当想在 `src` 中使用此数据，并将其用于 `img` 或其他标签时。
		abort() —— 取消操作。
	读取过程中，有以下事件：
		loadstart —— 开始加载。
		progress —— 在读取过程中出现。
		load —— 读取完成，没有 error。
		abort —— 调用了 abort()。
		error —— 出现 error。
		loadend —— 读取完成，无论成功还是失败。
	读取完成后，我们可以通过以下方式访问读取结果：
		reader.result 是结果（如果成功）
		reader.error 是 error（如果失败）。

在 Web Workers 中可以使用 FileReaderSync
	有一种同步的 FileReader 变体，称为 FileReaderSync。读取方法 `read*` 不会生成事件，但是会像常规函数那样返回一个结果。仅在 Web Worker 中可用，因为在读取文件的时候，同步调用会有延迟，而在 Web Worker 中，这种延迟并不是很重要。它不会影响页面。



### 网络请求

#### Fetch
AJAX，对于JavaScript 的网络请求的总称术语。
多种方式向服务器发送网络请求，并从服务器获取信息。
fetch()请求
	let promise = fetch(url, [options])，//浏览器立即启动请求，并返回一个该调用代码应该用来获取结果的 promise。
		url —— 要访问的 URL。
		options —— 可选参数：method，header 等。无options则是简单的get请求，获取url的内容；
	典型的 fetch 请求由两个 await 调用组成：
		let response = await fetch(url, options); // 解析 response header
		let result = await response.json(); // 将 body 读取为 json
		或者以 promise 形式：
			fetch(url, options) .then(response => response.json()) .then(result => /* process result * /）
	获取响应的两个阶段
		第一阶段
			服务器发送响应头，promise内建的 Response class 对象对响应头进行解析。
			可检查响应头来检查 HTTP 状态以确定请求是否成功。
			若fetch无法建立http请求，则promise会reject
			response 的属性中看到 HTTP 状态：
				status —— HTTP 状态码，例如 200。
				ok —— 布尔值，如果 HTTP 状态码为 200-299，则为 true。
				headers —— 类似于 Map 的带有 HTTP header 的对象。
		第二阶段
			调用其他方法获取 response body；
				response.text() —— 读取 response，并以文本形式返回 response，
				response.json() —— 将 response 解析为 JSON 对象形式，
				response.formData() —— 以 FormData 对象（multipart/form-data 编码，参见下一章）的形式返回 response，
				response.blob() —— 以 Blob（具有类型的二进制数据）形式返回 response，
				response.arrayBuffer() —— 以 ArrayBuffer（低级别的二进制数据）形式返回 response。
				只能选择一种读取 body 的方法。
		Response header
			Response header 位于 response.headers 中的一个类似于 Map 的 header 对象。
			不是真正的 Map，但是它具有类似的方法，我们可以按名称（name）获取各个 header，或迭代它们
		Request header
			要在 fetch 中设置 request header，我们可以使用 headers 选项。它有一个带有输出 header 的对象。但有一些无法设置的header。保证 HTTP 的正确性和安全性，所以它们仅由浏览器控制。
			let response = fetch(protectedUrl, { headers: { Authentication: 'secret' } });
POST 请求
	创建一个 `POST` 请求，需要使用 `fetch` 选项：
		method —— HTTP 方法，例如 POST，
		body —— request body，其中之一：
			字符串（例如 JSON 编码的），
			FormData 对象，以 multipart/form-data 形式发送数据，
			Blob/BufferSource 发送二进制数据，
			URLSearchParams，以 x-www-form-urlencoded 编码形式发送数据，很少使用。
		let response = await fetch('/article/fetch/post/user', { method: 'POST', headers: { 'Content-Type': 'application/json;charset=utf-8' }, body: JSON.stringify(user) });
		如果请求的 body 是字符串，则 Content-Type 会默认设置为 text/plain;charset=UTF-8。
		但是，当我们要发送 JSON 时，我们会使用 headers 选项来发送 application/json，这是 JSON 编码的数据的正确的 Content-Type。
发送图片
	可以使用 Blob 或 BufferSource 对象通过 fetch 提交二进制数据。
	




#### FormData
FormData 对象用于捕获 HTML 表单，并使用 `fetch` 或其他网络方法提交。
FormData 对象
	表示 HTML 表单数据的对象。
	构造函数：
		let formData = new FormData([form]);
	如果提供了 HTML form 元素，它会自动捕获 form 元素字段。
	FormData 方法
		可以从 HTML 表单创建 new FormData(form)，也可以创建一个完全没有表单的对象，然后使用以下方法附加字段：
			formData.append(name, value)， 添加具有给定 `name` 和 `value` 的表单字段，
			formData.append(name, blob, fileName)，要发送文件，需要使用三个参数的语法，最后一个参数是文件名，一般是通过 `<input type="file">` 从用户文件系统中获取的。
			formData.set(name, value)，同append，但会移除同名字段后再添加
			formData.set(name, blob, fileName)，同append，但会移除同名字段后再添加
			formData.delete(name) —— 移除带有给定 name 的字段，
			formData.get(name) —— 获取带有给定 name 的字段值，
			formData.has(name) —— 如果存在带有给定 name 的字段，则返回 true，否则返回 false。
			for..of 循环迭代 formData 字段
	发送带有文件的表单
		表单始终以 Content-Type: multipart/form-data 来发送数据，这个编码允许发送文件。因此 `<input type="file">` 字段也能被发送，类似于普通的表单提交。
	发送具有 Blob 数据的表单
		以 `Blob` 发送一个动态生成的二进制数据很容易，例如图片。
		实际中更方便的是通过表单的形式发送，并带上附加字段。且服务器适合接收多部分编码的表单，而非原始二进制数据。
		可以用canvas.toBlob方法将图像转为blob数据再添加到表单中发送。




#### Fetch：下载进度
fetch 方法可以跟踪 下载 进度，但无法跟踪 **上传** 进度。
通过response.body 属性（是可以逐块提供body的特殊对象ReadableStream）跟踪下载进度。
	通过流读取器getreader，response.body.getReader().read();调用的结果是一个具有两个属性的对象：
		done —— 当读取完成时为 true，否则为 false。
		value —— 字节的类型化数组：Uint8Array。
读取response不能同时使用：流读取器 、response方法
依据进度读取结果示例
	通过流读取器 读取数据
	通过Content-Length header得到响应长度。
	调用 `await reader.read()`，直到它完成。
	将响应块收集到数组 `chunks` 中，chunksAll字节数组。
	使用内建的 TextDecoder 对象，解析字节成字符串。还可以JSON.parse。
	得到结果，字符串或blob形式或其他。并在过程中对进度进行了跟踪。




#### Fetch：中止（Abort）
AbortController内建对象
	可以中止fetch和其他异步任务。
	创建一个控制器
		let controller = new AbortController();
	方法：
		abort()，调用时：controller.signal 就会触发 abort 事件、controller.signal.aborted 属性变为 true。
	属性
		signal，可以在属性上设置事件监听器。
应用
	在fetch中使用
		取消fetch：将AbortController的signal属性作为fetch的可选参数进行传递、然后调用controller.abort()即可。（fetch会监听到signal上的abort事件然后终止请求，promise会返回error `AbortError` reject，然后我们再进行对错误的处理，如可放在try cahtch中）。
	AbortController 是可伸缩的
		AbortController可以一次取消多个fetch，或者多个异步任务，且只需要监听其 `abort` 事件。





#### Fetch：跨源请求
CORS：跨源资源共享
跨源请求
	使用script
		先使用全局函数接受数据；
		创建script标签<>，设置src=”http://another.com/weather.json?callback=gotWeather“
		远程服务器动态生成脚本，脚本调用我方全局函数，发送数据；
		安全可行。有些服务仍在使用；
两种跨源请求
	安全请求
		需满足两个条件
			安全的方法：GET，POST 或 HEAD
			安全的 header ——我们仅能设置：
				Accept，
				Accept-Language，
				Content-Language，
				Content-Type 的值为 application/x-www-form-urlencoded，multipart/form-data 或 text/plain。
		用于安全请求的 CORS
			浏览器发送带有源的 Origin header。服务器检查该源同一则在响应中特殊的 header Access-Control-Allow-Origin。值是允许的源。
		Response header
			对于跨源请求，js默认只能访问安全的response header：     其他header都会error。
					Cache-Control
					Content-Language
					Content-Type
					Expires
					Last-Modified
					Pragma
			访问其他header方式：服务器发送`Access-Control-Expose-Headers` header，
		与其他请求本质区别在于，自古可以使用 `<form>` 或 `<script>` 标签来实现安全请求。
	其他所有请求（非安全请求）
		具有其他的方法或者具有其他的 header的请求。
		可使用任何http方法： GET/POST、patch、delet或其他。
		对于非安全请求，浏览器会会在请求之前发出初步“预检”请求
			浏览器将具有以下 header 的 OPTIONS 请求发送到相同的 URL：
				Access-Control-Request-Method 有请求方法。
				Access-Control-Request-Headers 以逗号分隔的“非安全” header 列表。
			服务器应该响应状态码为 200 和 header：
				Access-Control-Allow-Methods 带有允许的方法的列表，
				Access-Control-Allow-Headers 带有允许的 header 的列表，
				Access-Control-Max-Age 带有指定缓存权限的秒数。
			然后，发送实际的请求，并应用之前的“安全”方案。
	凭据（cookie或http认证）
		一般js代码发起的跨源请求不会带来任何凭据。http请求一般是会附带该域的所有cookie。要在 `fetch` 中发送凭据，我们需要添加 `credentials: "include"` 选项。
		对于没有凭据的请求（默认不发送），服务器应该设置：
			Access-Control-Allow-Origin 为 * 或与 Origin 的值相同
		对于具有凭据的请求，服务器应该设置：
			Access-Control-Allow-Origin 值与 Origin 的相同
			Access-Control-Allow-Credentials 为 true

请求分为 3 种类型：
	同源请求。
	跨源请求。
	从 HTTPS 到 HTTP 的请求 (从安全协议到不安全协议)。



#### Fetch API
所有可能的 fetch 选项及其默认值：
	let promise = fetch(url, {
		methods: POST、、
		headers: {}
		body: {}    //formdata,string,blob,buffersource,
		referrer,
		referrerPolicy,
		mode,
		credentials,
		cache,
		redirect,
		integrity,
		keepalive,
		signal,
		window,
		});

referrer，referrerPolicy
	都作用于fetch如何设置 HTTP 的 `Referer` header。
		 `Referer` header：一般被自动设置，包含发出请求的页面的url；一般不重要且可能因为安全原因而删除或缩短；
	 referrer 选项允许设置任何 Referer（在当前域的），或者移除它。
referrerPolicy
	referrerPolicy 选项为 Referer 设置一般的规则。
	referrerPolicy 告诉浏览器针对各个请求类型的一般的规则。
			 
mode
	一种安全措施，可以防止偶发的跨源请求：
		"cors" —— 默认值，允许跨源请求，
		"same-origin" —— 禁止跨源请求，
		"no-cors" —— 只允许安全的跨源请求。
credentials
	credentials 选项指定 fetch 是否应该随请求发送 cookie 和 HTTP-Authorization header。
		"same-origin" —— 默认值，对于跨源请求不发送，
		"include" —— 总是发送，需要来自跨源服务器的 Access-Control-Allow-Credentials，才能使 JavaScript 能够访问响应，
		"omit" —— 不发送，即使对于同源请求。
cache
	默认地，fetch 请求使用标准的 HTTP 缓存。就是说，它遵从 Expires，Cache-Control header，发送 If-Modified-Since，等。就像常规的 HTTP 请求那样。
	cache 选项可以忽略 HTTP 缓存或者对其用法进行微调
redirect
	一般`fetch` 透明地遵循 HTTP 重定向，例如 301，302 等。
	redirect 选项允许对此进行更改：
		"follow" —— 默认值，遵循 HTTP 重定向，
		"error" —— HTTP 重定向时报错，
		"manual" —— 允许手动处理 HTTP 重定向。在重定向的情况下，我们将获得一个特殊的响应对象，其中包含 response.type="opaqueredirect" 和归零/空状态以及大多数其他属性。
integrity
	integrity 选项允许检查响应是否与已知的预先校验和相匹配。
keepalive
	表示该请求可能会在网页关闭后继续存在。（如，需要收集一些使用页面的一些统计信息时）通常，当一个文档被卸载时（unloaded），所有相关的网络请求都会被中止。
	可以使用 window.onunload 事件来实现：在unload事件中fetch。
	额外限制
		- 无法发送兆字节的数据：`keepalive` 请求的 body 限制为 64KB。解决办法：需期以数据包的形式发送出去，或者可以并行执行多个 keepalive 请求，但它们的 body 长度之和不得超过 64KB。
		- 无法处理服务器响应，一般服务器也只发送空响应







#### URL 对象

内建的 URL 类提供了用于创建和解析 URL 的便捷接口。
一般使用字符串就行，不是非要使用url对象；

创建 URL 对象
	new URL(url, [base])；
		url —— 完整的 URL，或者仅路径（如果设置了 base），
		base —— 可选的 base URL：如果设置了此参数，且参数 url 只有路径，则会根据这个 base 生成 URL。
		let url1 = new URL('https://javascript.info/profile/admin');     //这两者一样。
		let url2 = new URL('/profile/admin', 'https://javascript.info');
 URL 组件
	 ![[Pasted image 20230706210238.png||400]]
	 href 是完整的 URL，与 url.toString() 相同
	protocol 以冒号字符 : 结尾
	search —— 以问号 ? 开头的一串参数
	hash 以哈希字符 # 开头
	如果存在 HTTP 身份验证，则这里可能还会有 user 和 password 属性：http://login:password@site.com（图片上没有，很少被用到）。
可以将 URL 对象传递给网络（和大多数其他）方法，而不是字符串
	可以在 fetch 或 XMLHttpRequest 中使用 URL 对象，。几乎可以在任何需要 URL 字符串的地方都能使用 `URL` 对象。

创建具有给定搜索参数的 url
	如：new URL('https://google.com/search?query=JavaScript')
	当参数中包含空格，非拉丁字母时，则通过url.searchParams属性（URLSearchParams 类型的对象。）进行编码，提供的方法
		url.searchParams.append(name, value) —— 按照 name 添加参数，
		url.searchParams.delete(name) —— 按照 name 移除参数，
		url.searchParams.get(name) —— 按照 name 获取参数，
		url.searchParams.getAll(name) —— 获取相同 name 的所有参数（这是可行的，例如 ?user=John&user=Pete），
		url.searchParams.has(name) —— 按照 name 检查参数是否存在，
		url.searchParams.set(name, value) —— set/replace 参数，
		url.searchParams.sort() —— 按 name 对参数进行排序，很少使用，
		……并且它是可迭代的，类似于 Map。
编码（encoding）
	RFC3986 标准定义了 URL 中允许哪些字符，不允许哪些字符。不允许的字符必须编码。
编码字符串
	可以使用url对象也可以使用字符串，但当使用字符串，则需要手动编码/解码特殊字符。
	用于编码/解码 URL 的内建函数：
		encodeURI —— 编码整个 URL。
		decodeURI —— 解码为编码前的状态。
		encodeURIComponent —— 编码 URL 组件，例如搜索参数，或者 hash，或者 pathname。
		decodeURIComponent —— 解码为编码前的状态。
		例：
			let url = encodeURI('http://site.com/привет');
			alert(url); // http://site.com/%D0%BF%D1%80%D0%B8%D0%B2%D0%B5%D1%82



#### XMLHttpRequest
XMLHttpRequest 是一个内建的浏览器对象
	它允许使用 JavaScript 发送 HTTP 请求。
	可以操作任何数据，不仅是XML格式，还可以上传下载文件，跟踪进度。
	与fetch
		fetch更现代，XMLHttpRequest某些时候弃用；
		还使用XMLHttpRequest的场景
			历史原因，支持现有的使用了 `XMLHttpRequest` 的脚本。
			兼容旧浏览器，同时不想用 polyfill，（例如为了使脚本更小）。
			 fetch 目前无法做到的事情，例如跟踪上传进度。
XMLHttpRequest 基础
	有两种执行模式：同步和异步（最常用）；
	异步
		发送请求，3个步骤
			创建 `XMLHttpRequest`：let xhr = new XMLHttpRequest();    该构造器无参数；
			初始化，通常就在 `new XMLHttpRequest` 之后，只是配置请求。
				xhr.open(method, URL, [async, user, password])
					method —— HTTP 方法。通常是 "GET" 或 "POST"。
					URL —— 要请求的 URL，通常是一个字符串，也可以是 URL 对象。
					async —— 如果显式地设置为 false，那么请求将会以同步的方式处理，我们稍后会讲到它。
					user，password —— HTTP 基本身份验证（如果需要的话）的登录名和密码
			发送请求
					xhr.send([body])；  可以是blob和buffersource对象
					建立连接，将请求发送到服务器。
					body包含了request body。GET 没有 request body。
			监听 xhr 事件以获取响应。
					常用的3个事件
						load —— 当请求完成（即使 HTTP 状态为 400 或 500 等），并且响应已完全下载。
						error —— 当无法发出请求，例如网络中断或者无效的 URL。
						progress —— 在下载响应期间定期触发，报告已经下载了多少。
			从xhr 属性中接收响应结果
					status数字：响应状态码
					statusText字符串：http状态消息，OK、not found、。
					response（或旧版本的responseText）：服务器 response body。
					timeout：指定超时时间；
			响应类型
					可以使用 xhr.responseType 属性来设置响应格式：
						""（默认）—— 响应格式为字符串，
						"text" —— 响应格式为字符串，
						"arraybuffer" —— 响应格式为 ArrayBuffer（对于二进制数据，请参见 ArrayBuffer，二进制数组），
						"blob" —— 响应格式为 Blob（对于二进制数据，请参见 Blob），
						"document" —— 响应格式为 XML document（可以使用 XPath 和其他 XML 方法）或 HTML document（基于接收数据的 MIME 类型）
						"json" —— 响应格式为 JSON（自动解析）。
			XMLHttpRequest的状态xhr.readyState，随着处理进度变化
					UNSENT = 0; // 初始状态
					OPENED = 1; // open 被调用
					HEADERS_RECEIVED = 2; // 接收到 response header
					LOADING = 3; // 响应正在被加载（接收到一个数据包）
					DONE = 4; // 请求完成
			中止请求
				   可以随时终止请求，直接调用xhr.abort();即可；
				   会触发 abort 事件，且 xhr.status 变为 0。
	同步请求（几乎从不使用）
			将open方法中的async参数设置为false即可。
			表现：JavaScript 执行在 send() 处暂停，并在收到响应后恢复执行。（易阻塞页面）
	HTTP-header
			XMLHttpRequest 允许发送自定义 header，并且可以从响应中读取 header。
			HTTP-header 有三种方法：
				setRequestHeader(name, value)；使用给定的 `name` 和 `value` 设置 request header。
						例：xhr.setRequestHeader('Content-Type', 'application/json');
						有些header由浏览器专门管理，不允许被XMLHttpRequest更改；
						XMLHttpRequest一旦设置了header，无法撤销；
				getResponseHeader(name)，获取具有给定 name 的 header（Set-Cookie 和 Set-Cookie2 除外）。
				getAllResponseHeaders()，返回除 Set-Cookie 和 Set-Cookie2 外的所有 response header。
	POST，FormData
			建立POST请求时，使用内建的 FormData 对象。
			xhr.send(formData)；
				以 multipart/form-data 编码发送表单。
				喜欢josn，也可以使用 JSON.stringify 并以字符串形式发送，设置 header Content-Type: application/json。
	上传进度
			progress 事件仅在下载阶段触发。
			当POST内容时，先上传数据再下载响应。
			当上传内容较大时，可能需要上传进度。使用`xhr.upload`对象。（无方法）
			在上传时，`xhr.upload`会触发以下事件
				loadstart —— 上传开始。
				progress —— 上传期间定期触发。——无法用于恢复上传，因是在数据被发送时触发。适用于显示一个好看的进度条。
				abort —— 上传中止。
				error —— 非 HTTP 错误。
				load —— 上传成功完成。
				timeout —— 上传超时（如果设置了 timeout 属性）。
				loadend —— 上传完成，无论成功还是 error。
	跨源请求
		XMLHttpRequest 可以使用和 fetch 相同的 CORS 策略进行跨源请求。
		像 fetch 一样，默认情况下不会将 cookie 和 HTTP 授权发送到其他域。要启用它们，可以将 xhr.withCredentials 设置为 true：xhr.withCredentials = true;
	最常用的事件是加载完成（load），加载失败（error），或者我们可以使用单个 loadend 处理程序并检查请求对象 xhr 的属性，以查看发生了什么。
	readystatechange：仍存在，但已被代替。






#### 可恢复的文件上传
连接断开后文件的恢复上传。
大文件的恢复上传：需要上传进度提示时，采用XMLHttpRequest，fetch无法使用。
恢复上传
	先发出一个请求，需要知道服务器接收的字节数。
	算法：
		创建一个文件 id，以唯一地标识我们要上传的文件：
			let fileId = file.name + '-' + file.size + '-' + file.lastModified;
		向服务器发送一个请求，询问它已经有了多少字节
			服务器通过 X-File-Id header 跟踪文件上传。应该在服务端实现。
			如果服务器上尚不存在该文件，则服务器响应应为 0。
		使用 Blob 和 slice 方法来发送从 startByte 开始的文件：
		服务器应该检查其记录，如果有一个上传的该文件，并且当前已上传的文件大小恰好是 X-Start-Byte，那么就将数据附加到该文件。




#### 长轮询（Long polling）
长轮询
	与服务器保持持久连接的最简单的方式。不使用任何特定的协议。
常规轮询（不好用）
	定期轮询：
		定期向服务器发出请求，从服务器获取新信息的最简单的方式。
		服务器首先通知自己，客户端处于在线状态，然后 —— 发送目前为止的消息包。
		缺点：
			间隔最多为10s；
			即使没有消息，服务器也会每隔 10 秒被请求轰炸一次，性能负担大。
长轮询（更好）
	可以无延迟地传递消息。
	流程为：
		请求发送到服务器。
		服务器在有消息之前不会关闭连接。
		当消息出现时 —— 服务器将对其请求作出响应。
		浏览器立即发出一个新的请求。
	如果连接丢失（如网络错误），浏览器会立即发送一个新请求。
	例：subscribe 函数发起了一个 fetch，然后等待响应，处理它，并再次调用自身。
	服务器架构必须能够处理许多挂起的连接。不能每个连接对应一个进程，易过多消耗内存。

使用场景
	消息很少的情况下，长轮询很有效。
	当消息很频繁时，请求-接收的图表会变成锯状状，且都是独立的请求，会有许多header、身份验证开销，可选择新的方式：Websocket 或 Server Sent Events。




#### WebSocket
WebSocket 协议：
	提供了一种在浏览器和服务器之间建立持久连接来交换数据的方法。数据可以作为“数据包”在两个方向上传递，而无需中断连接也无需额外的 HTTP 请求。
	例子：
		打开一个 WebSocket 连接：在 url 中使用特殊的协议 `ws` 创建 `new WebSocket`：
			let socket = new WebSocket("ws://javascript.info");
				协议wss://，类似于 WebSocket 中的 HTTPS，是加密的更可靠。
		建立socket后，再监听 socket 上的事件。一共有 4 个事件：
			open —— 连接已建立，
			message —— 接收到数据，
			error —— WebSocket 错误，
			close —— 连接已关闭。
			发生的事件顺序为：事件顺序为：open → message → close。
		发送数据
			socket.send(data)。data可以是文本(字符串)或二进制数据，包括blob，ArrayBuffer，不需要额外设置，直接发送即可。
		建立 WebSocket
			创建后（new WebSocket(url)），将立即开始连接。
			然后询问服务器是否支持WebSocket，则通过WebSocket 协议进行通信，（并非http协议）；
			创建时发出请求的浏览器的header
				GET /chat
				Host: javascript.info
				Origin: https://javascript.info   ，客户端页面的源
				Connection: Upgrade，    `Upgrade` —— 表示客户端想要更改协议。
				Upgrade: websocket，请求的协议是 “websocket”。
				Sec-WebSocket-Key: Iv8io/9s+lYFgZWcXczP8Q==   ，浏览器随机生成的安全密钥。
				Sec-WebSocket-Version: 13，    WebSocket 协议版本，当前为 13。
			若服务器同意切换为 WebSocket 协议，服务器应该返回响应码 101：
					101 Switching Protocols
					Upgrade: websocket
					Connection: Upgrade
					Sec-WebSocket-Accept: hsBlbuDTkk24srzEOTBUlZAlC2g=  ，是 Sec-WebSocket-Key，是使用特殊的算法重新编码的。浏览器使用它来确保响应与请求相对应。
			WebSocket的其他header，描述了扩展和子协议。
				Sec-WebSocket-Extensions：`deflate-frame` 表示浏览器支持数据压缩，扩展与传输数据有关，扩展了 WebSocket 协议的功能。由浏览器自动发送，其中包含其支持的所有扩展的列表。
				Sec-WebSocket-Protoco：soap, wamp 表示我们不仅要传输任何数据，还要传输 SOAP 或 WAMP协议中的数据，描述了我们将要使用的数据格式。
			服务器应该使用同意使用的协议和扩展的列表进行响应。
		数据传输
			WebSocket 通信由 “frames”（即数据片段）组成，可以从任何一方发送，并且有以下几种类型：
					“text frames” —— 包含各方发送给彼此的文本数据。
					“binary data frames” —— 包含各方发送给彼此的二进制数据。
					“ping/pong frames” 被用于检查从服务器发送的连接，浏览器会自动响应它们。
					还有 “connection close frame” 以及其他服务 frames。
					浏览器里，我们仅直接使用文本或二进制 frames。
			WebSocket .send() 方法可以发送文本或二进制数据。
			接收数据时，文本以字符串形式呈现，二进制数据可由socket.binaryType 属性设置，默认为 `"blob"`。
		限速
			当发送大量数据，但网速慢时，可以反复调用socket.send(data)，数据被缓存在内存中，再在网速允许下发出。
			socket.bufferedAmount 属性存储了已缓存的字节数，
				可检查它以判断socket是否可以用于传输。
		连接关闭
			当任意一方要关闭连接时，会发送一个connection close frame。
				socket.close([code], [reason]);
						code 是一个特殊的 WebSocket 关闭码（可选），类似Http码。
							1000 —— 默认，正常关闭（如果没有指明 code 时使用它），
							1006 —— 没有办法手动设定这个数字码，表示连接丢失（没有 close frame）。
							1001 —— 一方正在离开，例如服务器正在关闭，或者浏览器离开了该页面，
							1009 —— 消息太大，无法处理，
							1011 —— 服务器上发生意外错误，
							……等。
						reason 是一个描述关闭原因的字符串（可选）
			对方会通过 close 事件处理器获取了关闭码和关闭原因，
		连接状态
			通过socket.readyState获取连接状态。
					0 —— “CONNECTING”：连接还未建立，
					1 —— “OPEN”：通信中，
					2 —— “CLOSING”：连接关闭中，
					3 —— “CLOSED”：连接已关闭。
WebSocket 自身并不包含重新连接（reconnection），身份验证（authentication）和很多其他高级机制。因此，有针对于此的客户端/服务端的库，并且也可以手动实现这些功能。
有时为了将 WebSocket 集成到现有项目中，人们将主 HTTP 服务器与 WebSocket 服务器并行运行，并且它们之间共享同一个数据库。对于 WebSocket 请求使用一个通向 WebSocket 服务器的子域 wss://ws.site.com，而 https://site.com 则通向主 HTTP 服务器。
当然，其他集成方式也是可行的。








#### Server Sent Events
Server-Sent Events 规范描述了一个内建的类 EventSource，它能保持与服务器的连接，并允许从中接收事件。连接是持久的。
对于有些应用，websocket大材小用。所有现代浏览器都支持。
WebSocket	                                              EventSource
	双向：客户端和服务端都能交换消息	      单向：仅服务端能发送消息
	二进制和文本数据                                      仅文本数据
	WebSocket 协议                                       常规 HTTP 协议
	需手动实现									 			支持自动重新连接

接收消息
	需创建
		let source = new EventSource(url, [credentials]);
			可选参数，{ withCredentials: true }，它允许发送跨源凭证。
	浏览器再连接到url，保持连接，等待事件，
	服务器响应状态码为200，header 为 `Content-Type: text/event-stream`，保持连接并以特殊格式写入消息，如：
				data: Message 1
				data: Message 2
				data: Message 3
				data: of two lines
				data: 后为消息文本，冒号后面的空格是可选的。
				消息以双换行符 \n\n 分隔。
				要发送一个换行 \n，我们可以在要换行的位置立即再发送一个 data:（上面的第三条消息）。
			实际开发中，一般用json编码复杂消息，对于每个这样的消息，都会生成 message 事件。
跨源请求
	EventSource 支持跨源请求，就像 fetch 和任何其他网络方法。总体跨源安全性与 fetch 以及其他网络方法相同。我们可以使用任何 URL
	远程服务器
		获取到 Origin header，并且必须以 Access-Control-Allow-Origin 响应来处理。
		要传递凭证，则在发送时应该设置附加选项 `withCredentials`。
重新连接
	每次重新连接之间有一点小的延迟，默认为几秒钟。
	重新连接前：
		如，浏览器从操作系统获取无网络连接，则等待网络可连接时再重试。
	服务器
		可使用 retry: 来设置需要的延迟响应时间（以毫秒为单位）。
		retry：可独立出现，也可与其他消息一起出现。
				例： retry: 15000
						data: Hello, I set the reconnection delay to 15 seconds
	服务器希望浏览器停止重新连接时：	
		服务器使用HTTP 状态码 204 进行响应。
	浏览器想关闭连接时
		应该调用 `eventSource.close()`
	拒绝重新连接情况有：并发出error事件。
		响应的Content-Type不正确
		HTTP 状态码不是 301，307，200 和 204
连接的中断
	当连接中断时（如网络原因）
		由于双方无法确认已发送和未收到的消息有哪些，想要恢复正确的连接则需在服务器发送的每个消息里加上id字段。如
				data: Message 1
				id: 1
		收到id消息时，浏览器设置 eventSource.lastEventId属性值为id；
		重新连接后客户端发送带有 `id` 的 header `Last-Event-ID`。服务器便可发送后面的消息。
		一条消息可以按任何顺序包含一个或多个字段，但是 id: 通常排在最后。
连接状态
	EventSource.readyState属性表示
			EventSource.CONNECTING = 0; // 连接中或者重连中
			EventSource.OPEN = 1;       // 已连接
			EventSource.CLOSED = 2;     // 连接已关闭

默认情况下 EventSource 对象生成三个事件：
		message —— 收到消息，可以用 event.data 访问。
		open —— 连接已打开。
		error —— 无法建立连接，例如，服务器返回 HTTP 500 状态码。
	服务器可以在 event: 中设置自定义事件名称。应该使用 addEventListener 来处理此类事件，而不是使用 `on<event>`。









### 在浏览器中存储数据

#### Cookie，document.cookie
cookie
	概述：直接存储在浏览器中的一小串数据。它们是 HTTP 协议的一部分。
			作为身份验证的使用过程
				用户登录
				使用响应 Set-Cookie HTTP-header 设置cookie（具有唯一会话标识符）。
				下次当请求被发送到同一个域时，浏览器会使用 Cookie HTTP-header 通过网络发送 cookie。
	cookie的访问与写入
		通过	document.cookie访问器访问
		通过document.cookie更新，不更新所有cookie，只更新提到的cookie，且一般使用内建的 encodeURIComponent 函数进行转义再写入。
			document.cookie = "user=John";
			document.cookie = encodeURIComponent(name) + '=' + encodeURIComponent(value);
		限制
				encodeURIComponent 编码后的 name=value 对，大小不能超过 4KB。因此，我们不能在一个 cookie 中保存大的东西。
				每个域的 cookie 总数不得超过 20+ 左右，具体限制取决于浏览器。
	cookie的选项（cookie的内容）
		path=/mypath， 
			设置了/mypath及其子页面才可以访问该cookie，默认值为当前路径，url必须为绝对路径。一般设为根目录。
		domain=site.com，
			设置可访问cookie的域（实际中一般无法设置任何域）且无法从另一个二级域访问 cookie。
			默认 cookie 仅在设置cookie的当前域可见。如果显式地设置了域，可以使 cookie 在该子域下可见，如，document.cookie = "user=John; domain=site.com"
		expires 或 max-age 
			设定了 cookie 过期时间。如果没有设置，则当浏览器关闭时 cookie 就会失效。
			expires，日期需要GMT时区格式，可用date.toUTCString 转换Date对象得到。
			max-age，替代选项，指明了 cookie 的过期时间距离当前时间的秒数。
		secure 
			由于cookie基于域而不区分协议，不设置secure选项，cookie在两种协议下互相都可见。设置secure选项以免cookie 的敏感数据暴露在http中协议发送的请求中，需仅在 HTTPS 下有效。
		samesite，
			如果请求来自外部网站，禁止浏览器发送 cookie。这有助于防止 XSRF 攻击。
			XSRF 攻击：跨网站请求伪造攻击。受害网站通过设定 XSRF保护 token进行防护。
			两个可能的值：
				samesite=strict（和没有值的 samesite 一样)
						从外部来到网站发出的请求，则含samesite=strict的cookie永不会被发送。
				samesite=lax
						从外部来到网站发出的请求也不会发送，有例外：同时满足安全的http方法和执行的顶级导航(iframe不行)，则可发送
		 httpOnly
			 禁止任何js访问cookie，无法以document.cookie访问，以防被攻击。
	cookie函数
		优于document.cookie。
		getCookie(name)：
			返回具有给定 name 的 cookie。
			获取 cookie 最简短的方式是使用 正则表达式。
		setCookie(name, value, options)：
			将 cookie 的 name 设置为具有默认值 path=/（可以修改以添加其他默认值）和给定值 value：
			setCookie('user', 'John', {secure: true, 'max-age': 3600});
		deleteCookie(name)；
			删除一个 cookie，我们可以给它设置一个负的过期时间来调用它。
		更新或删除一个 cookie 时，我们应该使用和设置 cookie 时相同的路径和域选项。
	第三方cookie
		由用户所访问的页面的域以外的域放置的，则称其为第三方 cookie。
		第三方 cookie 通常用于跟踪和广告服务。






#### LocalStorage，sessionStorage
对比cookie
	不会每次随请求发送到服务器。
	可以保存更多数据。
	通过js完成，不能让服务器通过HTTP header 设置。
	绑定到源，不同域、不同协议、不同端口有不同存储对象，不能互相访问。

概述
	Web 存储对象 localStorage 和 sessionStorage，可以在浏览器上存储键值对，键值必须是字符串(包含自动转换)，像map集合，也可按索引访问。
	localStorage、sessionStorage存储对象的方法与属性：
		方法
			setItem(key, value) —— 存储键/值对。
			getItem(key) —— 按照键获取值。
			removeItem(key) —— 删除键及其对应的值。
			clear() —— 删除所有数据。
			key(index) —— 获取该索引下的键名。
			遍历：
				不可迭代，不能用for...of
				用 Object.keys获取只属于自己的键
				for...in 循环包含原型中的属性，需用hasOwnProperty过滤。
				for()普通循环
		属性
			length —— 存储的内容的长度。

localStorage
	在同源的所有标签页和窗口之间共享数据。
	数据不会过期。它在浏览器重启甚至系统重启后仍然存在。
	最好不要用类对象形式访问。
		由用户生成的键，无法用类对象形式访问，需用getItem/setItem访问。
		以类对象形式更改数据时，无法触发storage事件。
sessionStorage
	使用频率低于localStorage。
	sessionStorage的数据对于同页面内容但不同标签页有不同的存储。
	同一标签页下的同源 iframe 之间是共享的。
	数据在页面刷新后仍保留，但浏览器重启后不保留。
storage事件
	当localStorage 或 sessionStorage中的数据更新后触发，且在所有能访问到存储对象的window对象上触发(如两个标签页)，除了导致数据更改的window对象（改变数据的当前标签页的window）。
	事件属性
		key —— 发生更改的数据的 key（如果调用的是 .clear() 方法，则为 null）。
		oldValue —— 旧值（如果是新增数据，则为 null）。
		newValue —— 新值（如果是删除数据，则为 null）。
		url —— 发生数据更新的文档的 url。
		storageArea —— 发生数据更新的 localStorage 或 sessionStorage 对象。
		



#### IndexedDB
概述
	浏览器内建的数据库，是客户端数据库，数据通常与浏览器设置、扩展程序等一起存储在访问者的主目录中。绑定到源，不同网站不能互相访问。
	适用于离线应用，可与 ServiceWorkers 和其他技术相结合使用。
	IndexedDB 的本机接口是基于事件的。
	是NoSQL数据库
	
		通过支持多种类型的键，来存储几乎可以是任何类型的值。
		支撑事务的可靠性。
		支持键值范围查询、索引。
		和 localStorage 相比，它可以存储更大的数据量。

使用数据库 
	连接数据库
		let openRequest = indexedDB.open(name, version);
			name —— 字符串，即数据库名称。
			version —— 一个正整数版本，默认为 1。
			返回 openRequest 对象。需要监听该对象上的事件：
				success：数据库准备就绪，openRequest.result 中有了一个数据库对象“Database Object”，可用于进一步调用。
				error：打开失败。
				upgradeneeded：数据库已准备就绪，但其版本已过时
			允许有许多不同名称，绑定到源（域/协议/端口），不同网站无法互相访问。
IndexedDB具有内建的模式版本控制机制（服务器数据库则没有）
	当发布新版本应用程序时，访问该网页时，需更新该数据库。
		触发特殊事件upgradeneeded场景：
			当本地数据库低于open指定版本时，可根据需要升级数据结构。
			数据库还不存在时，会触发事件，执行初始化。
		无法使用较旧的 open 调用版本打开数据库
			如：当用户加载了一个过时的 JavaScript 代码时（加载代理缓存中的js）发生，代码过时，数据库是最新的。
			解决：检查 `db.version` 并建议用户重新加载页面，使用正确的 HTTP 缓存头（header）来避免之前缓存的旧代码被加载，可永远避免。
	并行更新问题（较少发生）
		如：应用程序网站更新前后分别打开一个标签页时，第二标签页无法正常打开，openRequest对象发生block事件而非success
		解决：
			由于versionchange 事件会在“过时的”数据库对象上触发，可监听该事件并关闭旧数据库的连接（提示重新加载页面）。
			或通过block事件提醒用户关闭冲突标签页。
对象库
	概述
		类似表或集合，用于存储数据。
		可以存储任何数据类型，原始数据类型、复杂对象等（除循环引用的对象，该对象也不可序列化，也不能 JSON.stringify）。
		IndexedDB使用标准序列化算法进行克隆和存储对象，类似 JSON.stringify。
		库中每个值必须有唯一的键key。
		键的类型必须为数字、日期、字符串、二进制或数组，是唯一的标识符，通过键来搜索/删除/更新值。
	创建对象库
		db.createObjectStore(name[, keyOptions]);             //db.createObjectStore('books', {keyPath: 'id'});
			name 是存储区名称，例如 "books" 表示书。
			keyOptions 是具有以下两个属性之一的可选对象：
				keyPath —— 对象属性的路径，IndexedDB 将以此路径作为键，例如 id。
				autoIncrement —— 如果为 true，则自动生成新存储的对象的键，键是一个不断递增的数字。
	对象库的更改
		在upgradeneeded处理程序中，在创建数据库时才可**创建/修改**对象库。
		upgradeneeded之外，在更新数据库时，才可创建/删除/更改对象库。
	数据库版本升级方法
		逐步实现每个版本的升级。
		检查数据库，用db.objectStoreNames获取对象库列表，该对象是一个 DOMStringList 提供 contains(name) 方法来检查 name 是否存在，再根据存在和不存在的内容进行更新。（适用于小型数据库。）
	两种存储值的方法：
		put(value, [key]) 
			将 value 添加到存储区。仅当对象库没有 keyPath 或 autoIncrement 时，才提供 key。如果已经存在具有相同键的值，则将替换该值。
		add(value, [key]) 
			与 put 相同，但是如果已经有一个值具有相同的键，则请求失败，并生成一个名为 "ConstraInterror" 的错误。
	对象库的两种搜索类型
		通过键值或键值范围。在我们的 “books” 存储中，将是 book.id 的值或值的范围。
		通过另一个对象字段，例如 book.price。这需要一个额外的数据结构，名为“索引（index）”。
		通过 key 搜索
			支持精确的键值和被称为“值范围”的搜索方法 —— IDBKeyRange 对象，指定一个可接受的“键值范围”。
				IDBKeyRange.lowerBound(lower, [open]) 表示：≥lower（如果 open 是 true，表示 >lower）
				IDBKeyRange.upperBound(upper, [open]) 表示：≤upper（如果 open 是 true，表示 <upper）
				IDBKeyRange.bound(lower, upper, [lowerOpen], [upperOpen]) 表示: 在 lower 和 upper 之间。如果 open 为 true，则相应的键不包括在范围中。
				IDBKeyRange.only(key) —— 仅包含一个键的范围 key，很少使用。
		通过索引字段搜索
			创建一个名为“索引（index）”的附加数据结构
			objectStore.createIndex(name, keyPath, [options]);
				name —— 索引名称。
				keyPath —— 索引应该跟踪的对象字段的路径（我们将根据该字段进行搜索）。
				option —— 具有以下属性的可选对象：
					unique —— 如果为true，则存储中只有一个对象在 keyPath 上具有给定值。如果我们尝试添加重复项，索引将生成错误。
					multiEntry —— 只有 keypath 上的值是数组时才使用。这时，默认情况下，索引将默认把整个数组视为键。但是如果 multiEntry 为 true，那么索引将为该数组中的每个值保留一个存储对象的列表。所以数组成员成为了索引键。
	从存储中删除
		delete 方法查找要由查询删除的值，调用格式类似于 getAll
			delete(query) —— 通过查询删除匹配的值。
	光标（Cursors）
		光标是一种特殊的对象，它在给定查询的情况下遍历对象库，一次返回一个键/值，从而节省内存。
		对象库是按键在内部排序的，因此光标按键顺序（默认为升序）遍历存储。
		let request = store.openCursor(query, [direction]);
			query 是一个键值或键值范围，与 getAll 相同。
			direction 是一个可选参数，使用顺序是：
				"next" —— 默认值，光标从有最小索引的记录向上移动。
				"prev" —— 相反的顺序：从有最大的索引的记录开始下降。
				"nextunique"，"prevunique" —— 同上，但是跳过键相同的记录 （仅适用于索引上的光标，例如，对于价格为 5 的书，仅返回第一本）。
			光标对象的主要区别在于 request.onSuccess 多次触发：每个结果触发一次。
		主要的方法
			advance(count) —— 将光标向前移动 count 次，跳过值。
			continue([key]) —— 将光标移至匹配范围中的下一个值（如果给定键，紧接键之后）。
	Promise 包装器
		将 onsuccess/onerror 添加到每个请求是一项相当麻烦的任务。我们可以通过使用事件委托（例如，在整个事务上设置处理程序）来简化我们的工作，但是 async/await 要方便的多。
		轻便的承诺包装器，使用 promisified IndexedDB 方法创建全局 idb 对象。
		错误处理
		“非活跃事务”陷阱
		获取本机对象

事务
	一组操作，要么全部成功，要么全部失败。事务可以保证同时完成。
	1、启动事务
		db.transaction(store[, type]);
			store 是事务要访问的库名称，例如 "books"。如果我们要访问多个库，则是库名称的数组。
			type – 事务类型，以下类型之一：
				readonly —— 只读，默认值。
				readwrite —— 只能读取和写入数据，而不能 创建/删除/更改 对象库。
		versionchange事务类型。
			可做任何事情，不可被创建，打开数据库时会自动为 upgradeneeded 处理程序创建 versionchange 事务。
	2、将项目添加到库
			创建事务；
			使用 transaction.objectStore(name)，获取存储对象。
			执行对对象库 books.add(book) 的请求
			处理请求 成功/错误。
	事务的自动提交
		当所有事务的请求完成，并且 微任务队列 为空时，它将自动提交。
		事务自动提交原则有一个重要的副作用。不能在事务中间插入 fetch, setTimeout 等异步操作。IndexedDB 不会让事务等待这些操作完成。
	错误处理
		如，写入请求可能会失败。
			失败的请求将自动中止事务，并取消所有的更改。
		事件委托
			IndexedDB 事件冒泡：请求 → 事务 → 数据库。




### 动画

#### 贝塞尔曲线
用于计算机图形绘制形状，CSS 动画和许多其他地方。
贝塞尔曲线由控制点定义
	控制点不总是在曲线上
	曲线的阶次等于控制点的数量减一
	曲线总是在控制点的凸包内部。———（可优化相交测试，凸包不相交，曲线不相交。）
贝塞尔曲线的两种定义方式
	数学方程式定义
	使用绘图过程：德卡斯特里奥算法
贝塞尔曲线的优点：
	我们可以通过控制点移动来用鼠标绘制平滑线条。
	复杂的形状可以由多条贝塞尔曲线组成。
用途：
	在计算机图形学，建模，矢量图形编辑器中。字体由贝塞尔曲线描述。
	在 Web 开发中 — 用于 Canvas 上的图形和 SVG 格式。顺便说一下，上面的“实时”示例是用 SVG 编写的。它们实际上是一个 SVG 文档，被赋予不同的控制点做参数。你可以在单独的窗口中打开它并查源码：demo.svg。
	在 CSS 动画中描述动画的路径和速度。



#### css动画
不借助js画出简单的动画
CSS 过渡
	改变某个属性，然后所有流畅的动画都由浏览器生成。
	定义属性，及其动态变化的方式，属性变化时，浏览器则绘制出相应动画。
	四个属性描述过渡
		transition-property
		transition-duration
		transition-timing-function
		transition-delay
css动画
	优点
		简单的事，简单地做。
		快速，而且对 CPU 造成的压力很小。
	不足
		JavaScript 动画更加灵活。它们可以实现任何动画逻辑，比如某个元素的爆炸效果。
		不仅仅只是属性的变化。我们还可以在 JavaScript 中生成新元素用于动画





#### JavaScript动画
JavaScript 动画可以处理 CSS 无法处理的事情。
JavaScript 动画应该通过 requestAnimationFrame 实现。该
	内建方法允许设置回调函数，以便在浏览器准备重绘时运行。那通常很快，但确切的时间取决于浏览器。
	当页面在后台时，根本没有重绘，因此回调将不会运行：动画将被暂停并且不会消耗资源。那很棒。



使用 setInterval
使用 requestAnimationFrame
	let requestId = requestAnimationFrame(callback);
		 callback 函数在浏览器每次重绘的最近时间运行。
结构化动画
时序函数
逆转：ease*



### Web components
用于创建独立组件的一组标准：自定义 HTML 元素，它们具有自己的属性和方法，封装好的 DOM 和样式。
组件化结构
	开发复杂软件的原则是：不要让软件复杂。
让复杂的事情简单化的架构才是好架构。
一个组件有：
	自己的 JavaScript 类。
	DOM 结构，并且只由自己的类管理，无法被外部代码操作。（「封装」原则）。
	CSS 样式，作用在这个组件上。
	API：事件，类方法等等，让组件可以与其他组件交互。

浏览器已经原生支持了「Web Components」
	Custom elements —— 用于自定义 HTML 元素.
	Shadow DOM —— 为组件创建内部 DOM，它对外部是不可见的。
	CSS Scoping —— 申明仅应用于组件的 Shadow DOM 内的样式。
	Event retargeting 以及更多的小东西，让自定义组件更适用于开发工作。
	




#### Custom elements（自定义标签）
我们可以通过描述带有自己的方法、属性和事件等的类来创建自定义 HTML 元素。
Custom elements 有两种：
	Autonomous custom elements （自主自定义标签） —— “全新的” 元素, 继承自 HTMLElement 抽象类.
	Customized built-in elements （自定义内建元素） —— 继承内建的 HTML 元素，比如自定义 HTMLButtonElement 等。需要多一个 `.define` 参数，同时 `is="..."` 在 HTML 中：




#### 影子 DOM（Shadow DOM）
为了封装，可以让一个组件拥有自己的「影子」DOM 树。
 DOM 树不能在主文档中被任意访问，可能拥有局部样式规则，还有其他特性。
Shadow DOM 是创建组件级别 DOM 的一种方法。
	shadowRoot = elem.attachShadow({mode: open|closed}) —— 为 elem 创建 shadow DOM。如果 mode="open"，那么它通过 elem.shadowRoot 属性被访问。
	我们可以使用 innerHTML 或者其他 DOM 方法来扩展 shadowRoot。
Shadow DOM 元素：
	有自己的 id 空间。
	对主文档的 JavaScript 选择器隐身，比如 querySelector。
	只使用 shadow tree 内部的样式，不使用主文档的样式。



#### 模板元素（`<template>`）
- `<template>` 的内容可以是任何语法正确的 HTML。
- `<template>` 内容被视为“超出文档范围”，因此它不会产生任何影响。
- 我们可以在JavaScript 中访问 `template.content` ，将其克隆以在新组件中重复使用。

`<template>` 标签非常独特，因为：
	- 浏览器将检查其中的HTML语法（与在脚本中使用模板字符串不同）。
	- 但允许使用任何顶级 HTML 标签，即使没有适当包装元素的无意义的元素（例如 `<tr>` ）。
	- 其内容是交互式的：插入其文档后，脚本会运行， `<video autoplay>` 会自动播放。

`<template>` 元素不具有任何迭代机制，数据绑定或变量替换的功能，但我们可以在其基础上实现这些功能。





#### Shadow DOM 插槽，组成
许多类型的组件，例如标签、菜单、照片库等等，需要内容去渲染。



#### 给 Shadow DOM 添加样式
shadow DOM 可以引入样式，如 `<style>` 或 `<link rel="stylesheet">`。
局部样式可以影响：
	shadow 树,
	shadow 宿主（通过 :host-family 系列伪类），
	占槽元素（来自 light DOM），::slotted(selector) 允许选择占槽元素本身，但不能选择它们的子元素。
文档样式可以影响：
	shadow 宿主（因为它位于外部文档中）
	占槽元素及占槽元素的内容（因为它们同样位于外部文档中）
	当 CSS 属性冲突时，通常文档样式具有优先级，除非属性被标记为 !important，那么局部样式优先。

CSS 自定义属性穿透 shadow DOM。它们被用作 “勾子” 来设计组件的样式：
	组件使用自定义 CSS 属性对关键元素进行样式设置，比如 var(--component-name-title, `<default value>`) 。
	组件作者为开发人员发布这些属性，它们和其他公共的组件方法一样重要。
	当开发人员想要对一个标题进行样式设计时，他们会为 shadow 宿主或宿主上层的元素赋值 --component-name-title CSS 属性。





#### Shadow DOM 和事件（events）
Shadow tree 背后的思想是封装组件的内部实现细节。





### 正则表达式
提供了一种在文本中进行搜索和替换的强大的方式的模式。
使用
	 RegExp 对象
	 字符串方法






***
### 浏览器
#### Window 对象
	对象表示浏览器中打开的窗口
History 对象保存了当前窗口访问过的所有页面网址。通过 history.length 可以得出当前窗口一共访问过几个网址。 由于安全原因，浏览器不允许脚本读取这些地址，但是允许在地址之间导航。 浏览器工具栏的“前进”和“后退”按钮，其实就是对 History 对象进行操作。

**属性**
History 对象主要有两个属性。
- History.length：当前窗口访问过的网址数量（包括当前网页）
- History.state：History 堆栈最上层的状态值（详见下文）
**方法**
History.back()、History.forward()、History.go() 这三个方法用于在历史之中移动。
- `History.back()`：移动到上一个网址，等同于点击浏览器的后退键。对于第一个访问的网址，该方法无效果。
- `History.forward()`：移动到下一个网址，等同于点击浏览器的前进键。对于最后一个访问的网址，该方法无效果。
- `History.go()`：接受一个整数作为参数，以当前网址为基准，移动到参数指定的网址。如果参数超过实际存在的网址范围，该方法无效果；如果不指定参数，默认参数为0，相当于刷新当前页面。

 
#### Location 对象
Location 对象包含有关当前 URL 的信息。
Location 对象是 window 对象的一部分；
可通过 window.location.xxx 格式的相关属性对其进行访问。
	hash	返回一个URL的锚部分
	host	返回一个URL的主机名和端口
	hostname	返回URL的主机名
	href	返回完整的URL
	pathname	返回的URL路径名。
	port	返回一个URL服务器使用的端口号
	protocol	返回一个URL协议
	search	返回一个URL的查询部分，从？开始的url；
