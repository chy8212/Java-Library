

未解决的问题：
浏览器将rem转成px时有精度误差怎么办？
	浏览器在渲染时所做的舍入处理只是应用在元素的渲染尺寸上，其真实占据的空间依旧是原始大小。





CSS层叠样式表，规则集：选择器，属性，值。  **==区分大小写==**
```css
		h1,p,li.classname {
		    color: red;
		    font-size: 5em;
		}
		.classname{
			color:red;
		}
```
拥有W3C的CSS规范（specs），需理解查阅      
css实现的三种方式：最广泛——引用：文档开头链接css文件
					`<link rel="stylesheet" href="style.css">`

#### 引用CSS
4种方式
	内嵌样式表< style>，具体样式写在head的< style>标签中；
	内联样式，放在 body 内的元素中；
	外部样式表，在 head 中用 link 标签引入css文件，< link rel="stylesheet" href="./style.css">；   随页面同时加载；
	导入样式表@import，放在head中内嵌的  < style>   标签里
		@import "URL";
		@import url("URL");
		需定义在内嵌样式表里的第一行；
		可放在css文件内的第一行使用；
		等页面加载完成后再加载；
		css2后新增的；


#### 选择器
选择器种类 
	ID选择器：               \#id {}
	类选择器：               .class {}
	属性选择：              元素[属性名或属性条件] {}   、
	伪类选择器：           元素 : 伪类{}
	元素选择器：           元素 {}
	伪元素选择器：        元素 :: 伪元素 {}
	后代选择器：           元素 元素{} 
	相邻兄弟选择器：    元素+元素{}
	子选择器：               元素 > 元素 {}       //直接子元素选择  
	通配符选择器：        * {}  、       元素  * {}

伪类：     如   :hover，:focus，用于选择处于特定状态的元素的选择器（元素的状态、别的相关父子元素）
伪元素： 如  ::after，作用于所选择元素的**特定部分**定义一些样式；（元素之前之后等）
CSS 优先规则3：
	优先级关系：内联样式1000 > ID 选择器100 > 类选择器10 = 属性选择器 = 伪类选择器 > 标签选择器1 = 伪元素选择器1；
权重计算优先级：权重并非10进制，简单计算易出错。CSS 权重进制比较大
css3之前：伪类和伪元素用冒号：
css之后：伪类冒号：   伪元素双冒号 ::  


#### 长度单位
绝对长度单位
	px：像素（包括物理像素，css像素）；
	cm：厘米
	mm：毫米
	in：英寸
相对长度单位
	em：该元素字体大小的em是相对于父元素字体大小；该元素的width/height/padding/margin用em的话是相对于本元素的字体大小；
	rem：相对根元素html的字体大小；
	vw：相对于浏览器窗口的宽度



	vh：相对于浏览器窗口的高度
	vmin：vw 与 vh 中较小的值；
	vmax：vw 与 vh 中较大的值；
	%：各自对应父元素属性的百分百；
	ex：本元素字体小写字母x的高度；
	ch：本意是字体数字0的高度；

#### 文本格式化
操作元素中的文本；字符间距、对齐方式、缩进
对齐
	text-align：设置文本的水平对齐方式；
	vertical-align：设置文本的垂直对齐方式；
间距
	letter-spacing：设置字符间距；
	letter-spacing：设置字符间距；
	word-spacing：设置单词与单词之间的间距（对中文无效）；
text-indent：设置文本的缩进方式；
line-height：设置行高；
text-shadow：设置文本阴影；
direction：设置文本方向。
text-decoration：设置文本的装饰；
text-transform：设置文本中英文的大小写转换方式；
white-space：设置文本中空白的处理方式；



#### （宽度和高度）
width：设置元素内容区的宽度
height ：定义元素内容区的高度
max-width 和 max-height：
	不论 width 或 height 属性的实际值是多少，width 和 height 属性的实际值都会小于等于 max-width 和 max-height 属性的值。
min-width 和 min-height
	不论 width 或 height 属性的实际值是多少，width 和 height 属性的实际值都会大于等于 min-width 和 min-height 属性的值。



#### 盒子模型
概述
	把每个元素当成一个矩形盒子的思维模型，四个部分构成，分别为内容区(content）、内边距(padding）、边框(border）和外边距（margin）；
	css为四部分提供了相关的属性，设置达到效果；
		内容：     有width、height、overflow(5值) 三个属性；
		内边距：  设置背景属性时，可覆盖该区域；？
		边框：     主流浏览器的背景属性可覆盖该区域；
		外边距： 值可为负； 一般情况下，具有外边距的两块级盒子相邻时，距离计算时值小的外边距被舍弃；

CSS3中的盒模型有以下两种：     ————区别在于设置宽高时包含的范围不同；设置元素的样式box-sizing属性来选择哪一种；
	标准盒子模型：高和宽包含内容；
	IE盒子模型：高和宽包含内三层；


#### overflow
当元素的内容溢出指定高宽范围的区域时设置的属性；
	visible	，默认值，不处理，内容会在元素内容区之外显示；
	hidden	，隐藏溢出内容
	scroll，	隐藏溢出内容，左方和下方各创建滚动条展示全部内容；
	auto	，    如果出现内容溢出，左方创建滚动条展示全部内容；
	inherit， 从父元素继承 overflow 属性的值

#### display显示类型
控制元素的布局，每个元素都有不同默认值；常用的值有：
	none	隐藏元素，不占用空间，visibility:hidden隐藏但占用空间；
	block	将元素设置为块级元素，独占行且设宽高和内外边距；自动换行；
	inline	将元素设置为内联元素，行内不能设宽高，只能设水平方向的内外边距；不会自动换行共享一行
	inline-block	将元素设置为行内块元素，可设置宽高可共享一行；不会自动换行会平铺如水平展示列表；
	list-item	将元素设置为列表项目
	table	    此元素会作为块级表格来显示。
	box	                 CSS3 中新增的属性值，表示将对象设置为弹性伸缩盒（伸缩盒的最老版本）
	inline-box	     CSS3 中新增的属性值，表示将对象设置为内联元素级的弹性伸缩盒（伸缩盒的最老版本）
	flexbox	         CSS3 中新增的属性值，表示将对象设置为弹性伸缩盒（伸缩盒的过渡版本）
	inline-flexbox   CSS3 中新增的属性值，表示将对象设置为内联元素级的弹性伸缩盒（伸缩盒的过渡版本）
	flex	                  CSS3 中新增的属性值，表示将对象设置为弹性伸缩盒（伸缩盒的最新版本）
	inline-flex	      CSS3 中新增的属性值，表示将对象设置为内联元素级的弹性伸缩盒（伸缩盒的最新版本）
	inherit	从父元素继承 display 属性的值


#### visibility（元素可见性）
设置元素是否可见，有以下值：仍然占有空间
	visible	  默认值，是可见的
	hidden	  隐藏元素
	collapse	表格：主要用来隐藏表格的行和列，隐藏的行或列所占的空间可以被其他表格内容使用；其他元素，其效果等同于“hidden”
	inherit	  从父元素继承 visibility 属性的值


#### position定位
将元素脱离原本的文档流，按照不同类型的定位放置，position后的元素按照其原本的文档流放置。配合使用top、right、bottom、left四个属性；具有后3种定位元素具有z-index: auto，实际值=0；
	static：默认值，静态定位，在原本的文档流中；无需使用4属性；
	relative：相对定位，参照物为静态位置，处在文档流中；
	absolute：
		绝对定位，有单独层且文档流中不占空间，参照物为本元素最近的具有相对定位的父元素，否则参照浏览器窗口；源顺序中的后定位元素叠上前一个定位元素。
	fixed：固定定位，参照物为浏览器视口，位置始终不变；
	sticky：粘性定位，参照物先为静态位置，然后参照物改为浏览器视口；完全受限于父级因素；
		在设置position:sticky;时，必须再定义 top、bottom、right、left 四个属性之一，否则只会处于相对定位的状态；
		使用粘性定位元素的父元素不能定义overflow:hidden或者overflow:auto属性；
		父元素的高度不能低于粘性定位元素的高度；
		粘性定位的元素仅在其父元素内有效。
		还可以相对底部粘住；设置bottom


#### z-index 堆叠
z-index 属性仅在元素定义了 position 属性且属性值不为 static 时才有效。



#### float（浮动）
使元素脱离原本的位置，在父元素的内容区左右移动，直到碰到父元素内容区的边界或者其它浮动元素为止。浮动元素周围的文本或元素将环绕；
	left	元素向左浮动
	right	元素向右浮动
	none	默认值，元素不浮动
	inherit	从父元素继承 float 属性的值
只对非绝对定位的元素有效；
当元素设置了绝对定位或者 display 属性的值为 none 时，float 属性无效；
相邻的浮动元素，如果空间足够它们会紧挨在一起，排列成一行；
清除浮动
	元素浮动之后，会对周围的元素造成一定的影响，为了消除这种影响， 周围元素可设置clear 属性；
			left	左侧不允许浮动元素
			right	右侧不允许浮动元素
			both	左右两侧均不允许浮动元素
			none	默认值，允许浮动元素出现在左右两侧
			inherit	从父元素继承 clear 属性的值
	

清除浮动：在浮动元素下方的元素加上属性clear: left;left停止任何活动的左浮动 right停止右浮动both停止左右浮动。
- 清除浮动元素周围的盒子：如何清除包含浮动元素的盒子下方的元素的浮动效果。
	- 小技巧
		- clearfix：向包含浮动内容及其本身的盒子后方插入一些生成的内容，并将生成的内容清除浮动。.wrapper::after {content: ""; clear: both;display: block;}
		- 使用overflow：包裹元素的 overflow 属性设置为除 visible 外的其他值。***【创建了所谓的 块格式化上下文（BFC）】***
	- display: flow-root，创建了格式化上下文BFC。在包裹的盒子添加display属性。



####  @规则
CSS 中包含两种语法规则：
	由选择器、属性和值构成；p {  }
	@关键字，分为两种：
		常规规则：
			@关键字 rule，字符编码@charset，@import，命名空间@namespace
		嵌套规则：
			@关键字 { }，媒体查询@media，@page，特性查询@supports，@font-face。




#### @media 媒体查询
为不同的媒体类型（设备类型）定义样式
css提供了不同的关键字来表示对应的媒体类型，以及不同的属性来描述设备特征；
媒体查询的两种方式：
	在样式表中：用@media 或 @import 规则指定设备类型：
		@media screen and (max-width: 992px) { };
		@import url("css/print.css") print;
	在 < style>、< link>、< source>等标签或其他 HTML 元素中：使用media属性指定设备类型；
		< link rel="stylesheet" media="screen and (min-width: 900px)" href="widescreen.css">


#### 浏览加载网页
1. 浏览器载入html文件
2. html文件转化为DOM
3. 拉取html相关资源图片视频css js
4. 解析css文件应用到DOM节点
5. 规则应用于渲染树，再结构布局
6. 网页展示



#### 层叠
级联规则：冲突的选择器为同一类型时，样式表稍后声明的样式将覆盖以前的样式
专用规则：冲突中的选择器更具体时更有效。
CSS规则应用影响因素：
	资源顺序、
	优先级（id&类&元素按照百十分位计算加权的优先级）、
	重要程度
	内联样式：元素内声明，优先于所有普通样式
	!important：优先级大于id
	样式表顺序(越后越高优先级)
		用户代理样式表（浏览器）
		用户样式表
		作者样式表
		作者样式表important
		用户样式表important
		以后代理样式表important
	级联层@layer顺序：
		级联层之间的优先级按声明顺序（如第一行声明）决定
		层外常规样式（无important）高于级联层，按顺序累积排在所有层最后
		带有important样式优先级：前层(im)>后层(im)>未声明层(im)
		内联样式>作者所有样式，不受级联层规则影响。
层叠上下文、层叠等级、层叠顺序、z-index
	1、首先先看要比较的两个元素是否处于同一个层叠上下文中：
		1.1如果是，谁的层叠等级大，谁在上面（怎么判断层叠等级大小呢？——看“层叠顺序”图）。
		1.2如果两个元素不在统一层叠上下文中，请先比较他们所处的层叠上下文的层叠等级。
	2、当两个元素层叠等级相同、层叠顺序相同时，在DOM结构中后面的元素层叠等级在前面元素之上。
	层叠顺序图



#### flex布局（弹性布局/弹性盒子）

传统：盒模型布局：依赖三种属性： display 属性（文档流布局） + position 属性（定位布局） + float属性（浮动布局）
Flex：弹性布局，CSS3中的新布局模式；
		规定容器内元素是按行排列还是按列排列，(元素可以灵活弹性的行列浮动)；
容器：
		采用 Flex 布局的元素；
		所有子元素自动成为容器成员；
		容器默认存在两根轴；
		子元素：
			每个flex item，有对应的主轴交叉轴的size；主轴交叉轴设置；
用法
	display：flex、inline-flex、-webkit —XX子元素自动成为容器成员；**子元素的float、clear和vertical-align属性将失效**
	记得 Webkit 内核的浏览器，必须加上 -webkit 前缀。

容器的属性有：
	flex-direction： 决定容器里是按行排列还是按列排列；决定主轴是哪个及起始方向：row | row-reverse | column | column-reverse;
	flex-wrap ：      决定子元素是否可换行：nowrap | wrap | wrap-reverse;  不换行|| 换行在下方 ||换行在上方
	flex-flow：        flex-direction 和 flex-wrap 的简写形式：< flex-direction> || < flex-wrap>;
	justify-content：
		决定子元素在轴内按轴方向的对齐方式，定义子元素在主轴的对齐方式：flex-start | flex-end | center | space-between | space-around;    左右居中两端对齐等等；
	align-items      ：
		决定子元素在轴内垂直轴的方向上的对齐方式；定义子元素在交叉轴上的对齐方式：flex-start | flex-end | center | baseline | stretch;   靠顶靠底
	align-content：所有轴线及内容在容器内的对齐方式，上下左右；flex-start | flex-end | center | space-between | space-around | stretch;


子元素item属性有：
	flex-basis：
		子元素固定的主轴方向上的长度，之后会分配剩余空间，浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。
	flex-grow：  若空间剩余，该子元素扩大多少倍；该子元素占据剩余空间的相对于其他子元素的倍数；1：全子元素等比例  0：不放大
	flex-shrink：若空间不足，该子元素缩小多少倍；   1：全元素等比例缩小；0：不缩小；
	**flex**：前3个属性的简写；one | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]、默认值为0 1 auto；建议优先使用该属性，不用单独分开写
	align-self：允许单个项目有与其他项目不一样的对齐方式
	order：该子元素在容器中的排列顺序，越小越靠前，默认值为 0


#### grid 网格布局
二维布局，表格table布局差不多，用 CSS 控制的，不是使用 HTML 控制的；
使用：
	display： grid 或、inline-grid （行内某个元素内部为网格）、 subgrid（该元素父元素为网格，继承父元素的行和列的大小） ；
	所有子元素就会自动变成网格项目（grid item），然后设置列（grid-template-columns）和 行（grid-template-rows）的大小，设置 grid-template-columns 有多少个参数生成的 grid 列表就有多少个列。
	注：当元素设置了网格布局，子元素的float、display: inline-block、display: table-cell、vertical-align和column-*等设置都将失效。

fr 单位
	多少个片段，用于分配剩余空间，1fr，2fr，表示前者是后者的一半；【1fr 1fr】、【150px 1fr 2fr;】
auto-fill：自动填充；
auto关键字表示由浏览器自己决定长度。
网格线的名称：在grid-template-columns行列属性里，可设置网格线名称；  grid-template-columns: [c1] 100px [c2] 100px [c3] auto [c4];

grid容器上属性
	grid-template-columns  ：每一列的列宽; 绝对单位 || 相对单位;【可枚举 ||  repeat（重复次数 || auto-fill ||  X fr，重复的值) 】
	grid-template-rows        ：每一行的行高。绝对单位 || 相对单位；【网格线名称 || 可枚举 ||   repeat（重复次数 || auto，重复的值）】
	grid-template-areas：标明网格中哪些地方是区域并命名（每个区域的命名会影响网格线命名），值为多行的字符串，用点标记不使用的区域
	grid-template
	grid-column-gap   ：列间距
	grid-row-gap         ：行间距
	grid-gap                 ：列间距、行间距的简写
	justify-items：对齐方式，设置单元格里的内容的水平位置（左中右，作用于所有单元格）：start | end | center | stretch;  拉伸
	align-items  ：对齐方式，设置单元格内容的垂直位置（上中下）。start | end | center | stretch;
	place-items ：align-items属性和justify-items属性的合并简写形式。
	justify-content  ：对齐方式，整个网格在容器里水平位置，start | end | center | stretch | space-around | space-between | space-evenly;
	align-content    ：对齐方式，整个网格在容器里面的垂直位置
	place-content   ：align-content属性和justify-content属性的合并简写
	grid-auto-columns：      设置浏览器自动创建的多余网格的列宽和行高。不设置，则表格会自动设置新增行列的长度；
	grid-auto-rows：            设置浏览器自动创建的多余网格的列宽和行高。
	grid-auto-flow：             设置排列顺序为row先行后列，或column；row dense，表示"先行后列"，并且尽可能紧密填满
	grid：       grid-template-X，grid-auto-X，等6个属性的简写方式；
grid子项上属性
	grid-column-start     ：设置子元素左边框所在的网格线，1，2，3，4
	grid-column-end       ：设置子元素右边框所在的网格线，1，2，3，4
	grid-row-start            ：设置子元素上边框所在的网格线，1，2，3，4
	grid-row-end             ：设置子元素下边框所在的网格线，1，2，3，4
	grid-column               ：`grid-column-start`和`grid-column-end`的合并简写。     span关键字，表示跨越多少个网格。1 / span 2;
	grid-row                      ：`grid-row-start`属性和`grid-row-end`的合并简写形式。
	grid-area      ：指定项目放在哪一个区域。
	justify-self            对齐方式，设置单元格内容的水平位置（左中右）；只作用于单个单元格；
	align-self              对齐方式，设置单元格内容的垂直位置（左中右）；
	place-self            `align-self`属性和`justify-self`属性的合并简写形式。
   

#### 响应式布局（自适应布局）
让一个网站兼容不同的终端（设备），进行布局和外观的调整；
实现方式：
	CSS 中的媒体查询;
	JavaScript（使用成本比较高）;
	第三方开源框架如bootstrap；
媒体查询
	meta 标签设置（视口=设备宽度、缩放设置）
	针对不同的媒体类型（screen print）定义不同的 CSS 样式；

#### 响应式设计（同上）
RWD：允许 Web 页面适应不同屏幕宽度因素等，进行布局和外观的调整的一系列实践。描述 Web 设计的一种方式，非单独的一种技术。
- 历史网页布局：液态站点&&固定宽度站点。
- 响应式设计RWD：包含三种技术混合使用：液态网格、液态图像、媒体查询。
	- 媒介查询：@media screen and (min-width: 800px) {}。媒体查询，以及样式改变时的点，被叫做断点。移动优先设计（窄屏单栏布局，宽屏多栏布局）。
	- 灵活网格：布局转化为百分数。
- 现代布局技术：
	- 多个列
	- 伸缩盒
	- css网格
- 响应式图像：
- 响应式排版：
	- @media (min-width: 1200px)，设置不同情况下字体大小
	- 使用视口单位vm设置字体
	- 视口元标签<meta name="viewport" content="width=device-width,initial-scale=1">
- 媒体查询：媒体类型、   媒体表达式  、  css规则
	                  @media media-type and (media-feature-rule) { css}
            媒体特征：宽高、朝向、指点设备、与或非混合条件、





#### 常见布局实现
水平居中
	


#### css预处理器
功能
	文件切分：可以通过编译环节将切分后的文件重新合并为一个大文件，两边问题解决：小文件性能问题；大文件维护；
	模块化
	选择符嵌套
	变量
	运算
	函数
	Mixin：区别于函数；先定义，然后在需要的地方调用；
主流预处理器：主流的预处理语言主要是 Sass(变种 SCSS)、Less 和 Stylus


#### CSS sprites 雪碧图
就是融合了各种资源的图片，图片里面可能会有一个角色的一套动作、或是组成背景的不同内容的块 tile 等；使用的时候，通过把该张图片当做背景图片，通过不同的 background-position定位来展示的那部分图片。

作用
	**减少 HTTP 请求数量**，**页面渲染更快，降低服务器压力**。：当小图片过多时。
	**提前加载好需要用到的图片**。
缺点
	添加小图片维护困难
	只能作为背景图片，不能使用img元素
	使用background属性时对误差要求严格，每张图计算位置。















***
***
***


### 网格
- display: grid   网格布局：水平及垂直的线构成的一种布局模式。  行、列、沟槽。
- grid-template-columns设置网格列宽：100px，1fr(是比例单位，可用空间)。
- **网格间隙**：   设置行列间隙长度grid-gap，可用任意长度单位如百分百，但不可用fr。
- 重复构建轨道组：  repeat（2，1fr），直接配置某长度的多列。
- **显示网格与隐式网格**：隐式网格就是为了放显式网格放不下的元素，浏览器根据已经定义的显式网格自动生成的网格部分。grid-auto-rows和grid-auto-columns设置行列高。
- **minmax() 函数**，minmax(100px, auto)，可用于宽高度，内容尺寸大于 100 像素则会根据内容自动调整。
- **往网格放置元素的方式： 
	- **分割线** ：grid-column: 1 / 3;   grid-row: 1;
	- 方式：grid-template-areas
	```css
	grid-template-areas:
	    "header header"
	    "sidebar content"
	    "footer footer";
	- ```
	- 网格排列框架

#### 背景与边框
背景图片background-image：小角或平铺（可控制平铺方式background-repeat）
背景图像大小background-size:cover\contain
背景图像定位background-position：top和right

#### 处理不同方向的文本
writing-mode：横向-纵向、块与内联
物理属性与逻辑属性：
逻辑属性和逻辑值：内联尺寸，块级尺寸width：inline-size，height:block-size，逻辑外边距，内边距，边框

#### 组织CSS
注意代码风格规范
oocss（面向对象的css）
BEM：块级元素修饰符，
预处理工具saas，后处理工具

DOM
树形结构，元素属性文字分别形成父子节点与兄弟节点，节点关系。
浏览器不处理会跳过无法解析的css代码。

#### 样式化文本
字体：网页安全字体，字体栈，web字体。

#### 继承
部分css属性支持子元素继承父元素的样式
		可继承：color、font-family
		不可：width、margin、padding、border
控制继承：
		inherit：继承
		initial：初始值
		revert：重置为浏览器默认值
		revert-layer：重置为上一层叠层的值
		unset：自然值为继承值或初始值
重设所有属性值：all属性：inherit、initial、revert、unset