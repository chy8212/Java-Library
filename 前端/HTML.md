

网页文件的后缀有很多种，比如.html、.php、.jsp、.asp等
网站
	就是一个绑定了域名的文件夹，该文件夹中可以包含子文件夹以及各种各样的文件，这些文件都可以通过域名来访问。
	当然，你也可以不绑定域名，只要在服务器上设置某个文件夹提供 Web 服务，用户也可以通过 IP 地址来访问。

互联网上的所有服务器都是通过 IP 地址来定位的，域名只是 IP 地址的一种助记符，帮助用户记住网站的链接以及品牌。使用域名访问网站时，浏览器会先找到域名对应的 IP 地址，然后再通过 IP 地址请求服务器上的文件；这个过程叫做域名解析，是通过 DNS 服务器来完成的。
网站服务器
	服务器一般是不带显示器、键盘、音响等外设的，唯一用途就是运行网站，；——刀片；

静态页面和动态页面
	静态页面中，用户通过页面操作的过程就是通过浏览器使用HTTP协议向服务器发送一个请求（Request），告诉服务器我需要展示那个页面，服务器收到请求后，直接根据用户的需求直接从文件系统中取出相应的文件，返回给浏览器，浏览器解析后为用户展示下相应的页面。
	动态页面中，用户通过浏览器发送的请求到达服务器之后，服务器根据请求内容从数据库中调取相应的内容组合成一个虚拟的文件，然后将文件发送给浏览器，用户才得以看到定制化的内容。是基本的html语法规范与Java、VB、VC等程序设计语言、数据库编程等多种技术的融合

### 基础

HTML 版本
	1~ ~5
都是w3c制定的标准，用于网页内容的标签；

xhtml：可以理解为html+xml，用xml的语法来规范重新定义html，最终形式和html大同小异是能满足xml的html；
xml是用来传输数据；
html用来显示数据；
HTML5只是HTML4的扩展，其精髓在于JS这块；文档第一行， <!Doctype html>

#### HTML属性
通用属性
	id,title,class,style.....
专用属性
	< img> 标签就有 src 和 alt 两个专用属性；图像的路径，图像的路径
	< a> 标签也有 href 和 target 两个专用属性；链接的地址，新页面在浏览器中的打开方式；
自定义属性

``
< p class="editor-note">My cat is very grumpy< /p>
- 为元素添加属性 ：元素锚`<a>`，使内容为超链接。
	- href：声明超链接的 web 地址
	- title：为超链接声明额外的信息
	- target：属性用于指定链接如何呈现出来，`target="_blank"` 将在新标签页中显示链接
	- 布尔属性：没有值的属性或者只能有一个值，这个值一般与属性名称相同``
	 < input type="text" disabled="disabled" />
实体引用：在HTML中包含特殊字符`<`、`>`、`"`、`'` 和 `&`  。使用字符引用——表示字符的特殊编码：<：`&lt;`

#### 超链接标签< a>
从一个网页指向另一个目标的连接关系，可以是
	网页；
	本网页另一位置；
	图片、文件、应用程序；

#### 列表标签：< ul>< ol>< dl>
有序列表，使用 < ol> + < li> 标签
无序列表，使用 < ul> + < li> 标签
定义列表，使用 < dl> + < dt> + < dd> 标签
	用于创建定义列表。定义列表由标题（术语）和描述两部分组成，描述是对标题的解释和说明，标题是对描述的总结和提炼。
	描述列表
```html
		<dl>
			<dt>旁白</dt>
			<dd>描述补充注释念白</dd>
		</dl>
```


meta标签
	

#### 表单：< form>标签
通过表单中的提交按钮将表单数据提交给后端程序。
属性
	action 属性用来指明将表单提交到哪个页面；
	method ：属性表示使用哪个方式提交数据，包括 GET 和 POST 两种方式，它们两者的区别如下：
		GET：用户点击提交按钮后，提交的信息会被显示在页面的地址栏中。一般情况下，GET 提交方式中不建议包含密码，因为密码被提交到地址栏，不安全。
		POST：如果表单包含密码这种敏感信息，建议使用 POST 方式进行提交，这样数据会传送到后台，不显示在地址栏中，相对安全。
表单控件
	表单用来收集用户数据，这些数据需要填写在各种控件中；
	如，input、textarea、label、select、button、等等；



#### 表格
tr：行       
（th：标题     td：单元格 ）：属性colspan/rowspan="2"：该单元格的宽度或长度为2个单元格
为列单独提供样式：采用`<col>、<colgroup>`
```html
		<table>
		  <colgroup>
		    <col>
		    <col style="background-color: yellow">
		  </colgroup>
		  或应用到每一列
			<colgroup>
			  <col style="background-color: yellow" span="2">
			</colgroup>
		  <tr>
		    ...
		</table>
```
表格标题caption：放置在table标签下方，`<caption>标题</caption>`
`<thead>、<tbody>、<tfoot>`结构中的表头、正文、页脚：方便应用样式与布局。
可嵌套表（一般不建议）
标记行列：
	- scope属性：修饰th元素，scope=“col/colgroup/row/rowgroup”，标记单行/列或多行/列
	- id、headers属性：id修饰th，headers标记所属行列的th。



#### 块级元素和内联元素
块级元素
	元素总是在新行上开始；
	不设宽度，默认为当前浏览器窗口的宽度；
内联元素
	和其他元素会在同一行上显示；
	宽、高以及外边距和内边距（上下）都不可以改变；
	元素的宽度就是其中内容的宽度，且不可以改变；
	内联元素中只能容纳文本或者其他内联元素。



#### 布局
之前主要用div
H5提供专门布局的标签：header、section、nav、footer等等；



#### < iframe>标签：内联框架
可以将另一个网页嵌入到当前网页中。
嵌入技术
`<iframe>`:将其他 Web 文档嵌入到当前文档中
	- 属性：allowfullscreen：全屏模式
	- frameborder：是否绘制边框
	- src、width、height
	- sandbox：可提高安全性设置
```html
	<iframe src="https://developer.mozilla.org/zh-CN/docs/Glossary"
	        width="100%" height="500" frameborder="0"
	        allowfullscreen sandbox>
	  <p> <a href="https://developer.mozilla.org/zh-CN/docs/Glossary">
	    Fallback link for browsers that don't support iframes
	  </a> </p>
	</iframe>
```
iframe的安全隐患：
	- 单击劫持。只在必要时嵌入，或使用HTTPS（不能使用 HTTP 嵌入第三方内容）
	- 应始终使用沙盒sandbox（可限制沙盒内代码权限）。
	- 应配置CSP指令：内容安全策略，它提供一组 HTTP 标头（由 web 服务器发送时与元数据一起发送的元数据），旨在提高 HTML 文档的安全性。
`<embed> <object>`



#### < head>标签
用来定义有关 HTML 文档的元数据（描述数据的数据）以及所需资源的引用；
有 < title>、< base>、< link>、< style>、< meta>、< script> 和 < noscript> 等
< title>：必要且唯一；
	主要作用如下所示：
	在浏览器标题栏或者任务栏中显示标题；
	当将页面添加到收藏夹（书签）时提供标题；
	在搜索结果中显示页面标题。
< link rel="stylesheet" href="my-css-file.css" />
< base> 
	标签用于为页面中所有相对链接指定一个基本链接，是链接的前缀；
< meta> 
	标签用于提供有关 HTML 文档的元数据，例如页面有效期、页面作者、关键字列表、页面描述等信息。
	< meta> 标签定义的数据并不会显示在页面上，但却会被浏览器解析。
< noscript> 标签
	当用户的浏览器不支持 JavaScript 脚本或者禁用 JavaScript 脚本时，可以在 < noscript> 标签中定义一些内容来替代不能运行的 JavaScript 脚本或者给用户一些提示。除了 < script> 标签外，在 < noscript> 标签中可以包含任何 HTML 元素
< script src="my-js-file.js" defer></script>



## 多媒体
视频：`<video>`：注意格式与浏览器兼容
	- 属性：
		- src、controls（控件界面）：
		- width、height、autoplay（自动播放）、loop（循环播放）、muted（默认静音）、poster（广告图像的url）、preload（缓冲）
	- <source>标签：属性src，type
```html
	<video src="rabbit320.webm" controls>
	<video controls width="400" height="400"
       autoplay loop muted
       poster="poster.png">
		<source src="rabbit320.mp4" type="video/mp4">
		<source src="rabbit320.webm" type="video/webm">
		<p>你的浏览器不支持 HTML5 视频。可点击<a href="rabbit320.mp4">此链接</a>观看</p>
</video>
```
音频：`<audio>`：同上
```html
	<audio controls>
	  <source src="viper.mp3" type="audio/mp3">
	  <source src="viper.ogg" type="audio/ogg">
	  <p>你的浏览器不支持 HTML5 音频，可点击<a href="viper.mp3">此链接</a>收听。</p>
	</audio>
```
重置媒体：Javascript 中调用 [`load()`](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLMediaElement/load "load()")方法来重置媒体
音轨增删：可监听 AudioTrackList (en-US) 对象的 addtrack 事件（即HTMLMediaElement.audioTracks
显示音轨文本


超文本标记语言，定义内容结构，由”元素“组成，非编程语言，
![[Pasted image 20230227231722.png]]
浏览器解析HTML文件顺序：识别link和script元素并获取外部文件
```html
<!DOCTYPE html>  文档类型，链接一些 HTML 编写守则，用于保证文档正常读取。
<html>          根元素，包含整个页面内容
  <head>        头部，用来保存用户的一些的元数据，用户不可见，包含搜索引擎关键字，页面描述，css样式表，字符编码声明
    <meta charset="utf-8">   指定字符编码
    <title>My test page</title>   页面标题，浏览器标签页显示、收藏描述
  </head>
  <body>        用户可见页面内容
	<img src="images/firefox-icon.png" alt="My test image"> alt：图像的描述文本
  </body>
</html>
```
+ 标题`<h1,h2,h3,h4,h5,h6></h>`，h1顶级标题，最好只使用一次，h2章节标题，h3子标题。
+ 段落`<p></p>`   
- 强调``<em></em><strong></strong>,斜体与加粗。





# 元素

空元素：仅有一个标签，非标准开始结束标签，无内容且无结束标签。如< img>，仅表示嵌入图片。
图片`<img>`：替换元素（内容和尺寸由外部定义）。
		- alt属性：图片的文字描述，当图片无法显示时，搜索引擎可用。
		- title属性：悬停时显示
		- 位图：精确得包含了每个像素的位置和它的色彩信息，png，jpg，gif....
		- 矢量图：包含了图形和路径的定义，SVG格式（描述矢量图像的XML语言），无法使用 JavaScript 操作图像
				- 引入SVG代码
				- iframe嵌入SVG
		- 响应式图片：依据不同的媒体条件选择合适的图片（分辨率切换）
			- 创建响应式图片：
```html
	<img
	  srcset="elva-fairy-480w.jpg 480w, elva-fairy-800w.jpg 800w"   
	  定义了浏览器可选择的图片的设置及每个图片大小（每个图片的固有宽度）
	  sizes="(max-width: 600px) 480px,     媒体条件为真时选择480否则800
			 800px"
	  src="elva-fairy-800w.jpg"
	  alt="Elva dressed as a fairy" />
```
超链接a
		- 链接文档内某片段 
		- download属性：为下载资源时提供默认保存的文件名。
		- 电子邮件链接：可指定详细信息：主题，抄送，主题。
```html
		<a href="mailto:nowhere@mozilla.org">向 nowhere 发邮件</a>
		<h2 id="Mailing_address">邮寄地址</h2>
		<p>邮寄至<a href="contacts.html#Mailing_address">我们的地址</a></p>
```
列表`<ul>无序列表、<ol>有序列表、<li>列表项目、<dl>描述列表`  
```html
		<ul>
			<li>technologists</li>
			<li>thinkers</li>
			<li>builders</li>
		</ul>
```
  引用`<q> cite`
缩略语`<abbr>`  有悬停效果
```html
<p>我们使用 <abbr title="超文本标记语言">HTML</abbr> 来组织网页文档</p>
```
标记联系方式：`<address>`
上标下标：`<sup><sub>`
计算机代码的展示：`<code><pre><var><kbd><samp>`
标记时间和日期：`<time datetime>`
文档结构：`<header><nav><main><article><section><div>(尽可能少用无语义)<aside><footer>`
换行、水平分割线：`<br><hr/>`









# html调试