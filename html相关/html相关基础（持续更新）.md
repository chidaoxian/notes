# html相关的一些问题（持续更新）

秋招后的一些记录，看了很多东西想写下来，希望自己可以随时的查看，也希望有错误的地方大神可以指正。

## 1、H5新元素

### 新增元素：

header:定义页面的页眉

article:页面文章区域

aside:主题内容之外

section：定义页面的章节部分

footer：页面的页脚

audio:音频，src路径，controls显示控制面板，autoplay自动播放，loop循环

video:视频，src路径，controls显示控制面板，autoplay自动播放，loop循环，width宽度，height高度，poster当视频还未完全下载或用户还未点击播放前默认显示的封面，默认显示当前视频文件的第一帧。

source:浏览器的视频格式兼容

details：用于描述文档或文档某个部分区域，需要和summary结合使用

mark：带有记号的标签

nav：定义导航栏

progress：定义任务的进度，需要value和max值

fieldset：对表单元素进行分组，一般放在< form>标签里

### 表单的type属性（input）：

1、text:文本框

2、password:密码

3、email:邮件，提供电子邮件的完整验证 是否包含@符号，同时是否包含服务器名称。 

4、tel:为了能够在移动端打开数字键盘，限制用户只能输入数字

5、url:网址，验证只能输入网址，必须包含http://

6、number:只能输入数字，不能输入其他字符。max属性为最大值，min属性为最小值，value为默认值。

7、search:搜索框

8、range:范围，max最大值,min最小值,value默认值

9、color:拾色器。

10、time:时间

11、date:日期，弹出日历，选择日期。

12、datetime-local:日期时间

13、month：月份

14、week：星期

### 表单新增的其他属性：

1、placeholder:提示文字

2、autofocus：自动获取焦点

3、autocomplete:on打开，off关闭。前提是必须成功提交，必须有name属性

4、required：必须输入

5、pattern：正则表达式验证

6、multiple：允许多选

### 表单新增事件：

1、oninput:监听当前指定元素的内容，只要内容改变就触发改事件，类似onkeyup/onkeydown。不同点oninput事件不受鼠标或键盘影响，只要内容改变就触发。

2、oninvalid:当验证不通过时触发。

自定义属性。data-:

（1）data-开头

（2）data-后必须至少有一个字符，多个单词使用-连接

## 2、HTML5与HTML4的不同之处

1、文件类型声明（< !DOCTYPE>）仅有一型：< !DOCTYPE HTML>。

2、新的解析顺序：不再基于SGML（标准通用置标语言）

SGML语言特点：标准通用标记语言是一种描述语言的语言，定义了以电子形式表示文本的方法。它的特点有：

（1）、正式的，能允许验证文档的正确性。

（2）、结构化的，能够处理复杂的文档。

（3）、可扩充的，能够支持大型信息存储的管理。

3、新的元素：section, video, progress, nav, meter, time, aside, canvas, command, datalist, details, embed, figcaption, figure, footer, header, hgroup, keygen, mark, output, rp, rt, ruby, source, summary, wbr。
input元素的新类型：date, email, url等等。

4、input元素的新类型：date, email, url等等。

5、新的属性：ping（用于a与area）, charset（用于meta）, async（用于script）。

6、全域属性：id, tabindex, repeat。

7、新的全域属性：contenteditable, contextmenu, draggable, dropzone, hidden, spellcheck。

8、移除元素：acronym, applet, basefont, big, center, dir, font, frame, frameset, isindex, noframes, strike, tt。

## 3、html的语义化

1、语义化是指使用恰当语义的html标签，让页面具有良好的结构与含义。

2、比如 < p>标签就代表段落，< article>代表正文内容等等。

3、语义化的好处：

**开发者友好：**

（1）使用语义类标签增强了可读性。

（2）开发者也能够清晰地看出网页的结构。

（3）也更为便于团队的开发和维护。

**机器友好：**

（1）带有语义的文字表现力丰富。

（2）更适合搜索引擎的爬虫爬取有效信息。

（3）语义类还可以支持读屏软件，根据文章可以自动生成目录。

## 4、html、xhtml、xml有什么区别

1、HTML(超文本标记语言)：在html4.0之前HTML先有实现再有标准，导致HTML非常混乱和松散。

2、XML(可扩展标记语言)：主要用于存储数据和结构，可扩展，大家熟悉的JSON也是相似的作用，但是更加轻量高效，所以XML现在市场越来越小了。

3、XHTML(可扩展超文本标记语言)：基于上面两者而来，W3C为了解决HTML混乱问题而生，并基于此诞生了HTML5，开头加入< !DOCTYPE html>的做法因此而来，如果不加就是兼容混乱的HTML，加了就是标准模式。

## 5、什么是data-属性

这个很少被提及，但是还是可以简单说一下：

HTML的数据属性，用于将数据储存于标准的HTML元素中作为额外信息,我们可以通过js访问并操作它，来达到操作数据的目的。

## 6、doctype的作用是什么

1、DOCTYPE是html5标准网页声明。

2、且必须声明在HTML文档的第一行。

3、来告知浏览器的解析器用什么文档标准解析这个文档。

4、文档解析类型：

BackCompat：怪异模式，浏览器使用自己的怪异模式解析渲染页面。（如果没有声明DOCTYPE，默认就是这个模式）。

CSS1Compat：标准模式，浏览器使用W3C的标准解析渲染页面。

区别：

（1）标准模式(standards mode)：页面按照 HTML 与 CSS 的定义渲染。

（2）怪异模式(quirks mode)模式： 会模拟更旧的浏览器的行为。

（3）近乎标准(almost standards)模式： 会实施了一种表单元格尺寸的怪异行为（与IE7之前的单元格布局方式一致），除此之外符合标准定义。

## 7、html页面中meta的作用

1、meta是用来在HTML文档中模拟HTTP协议的响应头报文。

2、meta 的属性有两种：name和http-equiv。（可以见下一个总结：常用的meta标签）

name属性主要用于描述网页，对应于content（网页内容）。以便于搜索引擎机器人查找、分类。

http-equiv属性

## 8、常用的meta标签

### 简单解释：

1、meta标签由name和content两个属性来定义，来描述一个HTML网页文档的元信息。

2、charset，用于描述HTML文档的编码形式。

3、http-equiv，顾名思义，相当于http的文件头作用。

4、viewport，移动前端最熟悉不过，Web开发人员可以控制视口的大小和比例。

5、apple-mobile-web-app-status-bar-style,开发过PWA应用的开发者应该很熟悉，为了自定义苹果工具栏的颜色。

### 简单解释并不够：

1、定义和用法：< meta> 元素可提供有关页面的元信息（meta-information），比如针对搜索引擎和更新频度的描述和关键词。

< meta>标签位于文档的头部，不包含任何内容。< meta>标签的属性定义了与文档相关联的名称/值对。

2、提示和注释：注释：< meta> 标签永远位于 head 元素内部。

注释：元数据总是以名称/值的形式被成对传递的。

典型的情况是，meta 元素被用于规定页面的描述、关键词、文档的作者、最后修改时间以及其他元数据。

3、总结：< meta> 标签提供关于 HTML 文档的元数据。它不会显示在页面上，但是对于机器是可读的。可用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他 web 服务。

### 相关属性详细介绍：

**必须属性：**

content：

（1）some_text

（2）定义与 http-equiv 或 name 属性相关的元信息

（3）meta的必需属性是content，当然并不是说meta标签里一定要有content，而是当有http-equiv或name属性的时候，一定要有content属性对其进行说明。例如：

```javascript
< meta name="keywords" content="HTML,ASP,PHP,SQL">
//这里面content里的属性就是对keywords进行的说明，所以呢也可以理解成一个键值对吧，就是{keywords:"HTML,ASP,PHP,SQL"}。
```

**可选属性：**

http-equiv：值：content-type、expires、refresh、set-cookie。描述：把 content 属性关联到 HTTP 头部。

name：值：author、description、keywords、generator、revised、others。描述：把 content 属性关联到一个名称。

scheme：值：some_text。描述：	定义用于翻译 content 属性值的格式。

![1605951414446](C:\Users\CDX\AppData\Roaming\Typora\typora-user-images\1605951414446.png)

## 9、script标签中defer和async的区别

### defer：

等（HTML）文档解析完了执行（defer：浏览器指示脚本在文档被解析后执行，script被异步加载后并不会立刻执行，而是等待文档被解析完毕后执行。）

### async：

脚本加载完毕之后就执行（async：同样是异步加载脚本，区别是脚本加载完毕后立即执行，这导致async属性下的脚本是乱序的，对于script有先后依赖关系的情况，并不适用.）

### 注意：

默认同步加载完在继续往后执行。

## 10、img标签中srcset的作用以及picture标签

### srcset：

1、srcset提供了根据屏幕条件选取图片的能力。

2、可以设计响应式图片：

（1）使用两个新的属性srcset 和 sizes来提供更多额外的资源图像和提示。

（2）帮助浏览器选择正确的一个资源。

3、srcset 定义了我们允许浏览器选择的图像集，以及每个图像的大小。

4、sizes 定义了一组媒体条件（例如屏幕宽度）并且指明当某些媒体条件为真时，什么样的图片尺寸是最佳选择。

5、所以，有了这些属性，浏览器会些什么呢？

（1）查看设备宽度。

（2）检查 sizes 列表中哪个媒体条件是第一个为真 。

（3）查看给予该媒体查询的槽大小。

（4）加载 srcset 列表中引用的最接近所选的槽大小的图像.

### picture：

1、< picture>元素通过包含零或多个 < source> 元素和一个 < img>元素来为不同的显示/设备场景提供图像版本。

2、浏览器会选择最匹配的子 < source> 元素，如果没有匹配的，就选择 < img> 元素的 src 属性中的URL。然后，所选图像呈现在< img>元素占据的空间中。

3、picture同样可以通过不同设备来匹配不同的图像资源。

## 11、href与scr的区别

### href：

1、Hypertext Reference的缩写，超文本引用。

2、它指向一些网络资源，建立和当前元素或者说是本文档的链接关系。

3、在加载它的时候，不会停止对当前文档的处理，浏览器会继续往下走。常用在a、link等标签。

### src：

1、source的所写，表示的是对资源的引用。

2、它指向的内容会嵌入到当前标签所在的位置。

3、由于src的内容是页面必不可少的一部分，因此浏览器在解析src时会停下来对后续文档的处理，直到src的内容加载完毕。

4、常用在script、img、iframe标签中。

5、我们建议js文件放在HTML文档的最后面。如果js文件放在了head标签中，可以使用window.onload实现js的最后加载。

### 总结：

1、href用于建立当前页面与引用资源之间的关系（链接），而src则会替换当前标签。

2、遇到href，页面会并行加载后续内容。

3、而src则不同，浏览器需要加载完毕src的内容才会继续往下走。

## 12、link标签实现预加载

preload：是告诉浏览器页面必定需要的资源，浏览器一定会加载这些资源。

prefetch：是告诉浏览器页面可能需要的资源，浏览器不一定会加载这些资源。

## 13、块级元素和行内元素以及行内块级元素

![1605950597773](C:\Users\CDX\AppData\Roaming\Typora\typora-user-images\1605950597773.png)



### 块级元素 block：

1、每个块级元素都是独自占一行。

2、元素的高度、宽度、行高和边距都是可以设置的。

3、元素的宽度如果不设置的话，默认为父元素的宽度（父元素宽度100%）。

### 行内元素 inline：

1、每一个行内元素可以和别的行内元素共享一行，相邻的行内元素会排列在同一行里，直到一行排不下了，才会换行。 

2、行内元素的高度、宽度、行高及顶部和底部边距不可设置。 

3、元素的宽度就是它包含的文字或图片的宽度，不可改变。

### 行内块级元素 inline-block：

1、和其他行内或行内块级元素元素放置在同一行上。

2、元素的高度、宽度、行高以及顶和底边距都可设置。

### 元素类型转换display：

1、display：block ，定义元素为块级元素

2、display :  inline ，定义元素为行内元素

3、display：inline-block，定义元素为行内块级元素。

### 总结：

1、块级元素会独占一行，而内联元素和内联块元素则会在一行内显示。

2、块级元素和内联块元素可以设置 width、height 属性，而内联元素设置无效。

3、块级元素的 width 默认为 100%，而内联元素则是根据其自身的内容或子元素来决定其宽度。

## 14、offsetLeft、offsetWidth、scrollTop、scrollWidth、event.pageX属性

1、offsetHeight || offsetWidth = boder + padding + content（两者都是只读属性）

2、offsetLeft   offsetTop 一般是相对于offsetParent计算的，也就是第一个定位的父级。两者都是只读属性。

3、offsetTop 与 style.top 的差别：

（1）offsetTop 返回的是数字，而 style.top 返回的是字符串，除了数字外还带有单位：px。

（2）offsetTop 只读，而 style.top 可读写。

（3）若是没有给 HTML 元素指定过 top 样式，则 style.top 返回的是空字符串。

4、scrollTop、scrollLeft、scrollWidth、scrollHeight

5、event.clientX、event.clientY、event.pageX、event.pageY：

（1）event.clientX 是目标点距离浏览器可视范围的X轴坐标.

（2）event.clientY 是目标点距离浏览器可视范围的Y轴坐标.

（3）event.pageX 是目标点距离document最左上角的X轴坐标.

（4）event.pageY 是目标点距离document最左上角的Y轴坐标.

## 15、js如何给dom元素绑定事件，移除事件

### 1、兼容性很好    

```javascript
  div.onclick = test // 绑定事件  
  div.onclick = ''; // 移除事件
```

### 2、IE9以下不兼容

```javascript
    div.addEventListener('click',test,false)// 绑定事件
    div.removeEventListener('click',test,false)// 移除事件
```

### 3、IE独有

```javascript
    div.attachEvent('onclick',test) // 绑定事件
    div.detachEvent('onclick', test)// 移除事件
```

