# css相关（持续更新）

## 1、css选择器的优先级

### 1、基本概念

CSS选择器的优先级是：内联 > ID选择器 > 类选择器 （或属性选择器或伪类）> 标签选择器（或伪元素）。

### 2、一般计算方式

优先级仅有选择器决定，怎么个计算方法呢？

a、用a表示选择器中ID选择器出现的次数

b、用b表示类选择器，属性选择器和伪类选择器出现的总次数。

c、用c表示标签选择器、伪元素选择器出现的总次数

d、忽略通用选择器

e、然后计算a*100+b*10+c的大小，这就是优先级了。

权重：内联样式1000》id选择器100》class选择器10》标签选择器1

## 2、属性选择器

例如：可以只对有 href 属性的锚（a 元素）应用样式：a[href] {color:red;}

## 3、伪元素与伪类的区别

### 1、伪元素

**不存在在DOM文档中，是虚拟的元素，是创建新元素**

例如：

::before/::after（设置对象前/后发生的内容）

::first-letter       设置对象内的第一个字符的样式

::first-line     设置对象内的第一行的样式

::before      设置对象前（依据对象树的逻辑结构）发生的内容。用来和conntent属性一起使用

::after      设置对象后（依据对象树的逻辑结构）发生的内容。用来和conntent属性一起使用

::placeholder      设置对象文字占位符的样式

::selection      设置对象被选择时的颜色

### 2、伪类

**存在DOM文档中，逻辑上存在但在文档树中却无须标识的“幽灵”分类**

例如：

:link 设置超链接a在未被访问前的样式

:hover  设置元素在鼠标悬停时的样式 

:active  设置元素在被用户激活（在鼠标点击与释放直接发生的事情）时的样式

:focus  设置元素在成为输入焦点（该元素的onfocus事件发生）时的样式

## 4、link和@import的区别

1、link属于XHTML标签，而@import是CSS提供的。

2、因为@import是同步操作，只有把对应的样式导入后，才会继续向下执行，而link是异步的操作。

3、link没有兼容性：import只在IE 5以上才能识别，而link是XHTML标签，无兼容问题。

4、link方式的样式权重高于@import的权重。

5、@import不是dom可以控制的：使用dom控制样式时的差别。当使用javascript控制dom去改变样式的时候，只能使用link标签，因为@import不是dom可以控制的。

## 5、有哪些方式（CSS）可以隐藏页面元素

1、opacity:0（本质上是将元素的透明度将为0，就看起来隐藏了，但是依然占据空间且可以交互）。

2、visibility:hidden（ 与上一个方法类似的效果，占据空间，但是不可以交互了）。

3、overflow:hidden（这个只隐藏元素溢出的部分，但是占据空间且不可交互）。

4、display:none（这个是彻底隐藏了元素，元素从文档流中消失，既不占据空间也不交互，也不影响布局）。

5、z-index:-9999（ 原理是将层级放到底部，这样就被覆盖了，看起来隐藏了）。

5、transform: scale(0,0)（平面变换，将元素缩放为0，但是依然占据空间，但不可交互）。

## 6、使用display：inline-block产生的问题以及解决的方法

### 1、产生的问题

两个display：inline-block元素放到一起会产生一段空白

**产生的原因：**元素被当成行内元素排版的时候，元素之间的空白符（空格、回出换行等）都会被浏览器处理，根据CSS中white-space属性的处理方式（默认是normal，合并多余空白。），就是说原来HTML代码中的回车换行被换成一个空白符，在字体不为0的情况下空白符占据一定的宽度，所以出现了空隙。

### 2、解决的方法

（1）将元素的结束符和下一个标签写在同一行或把所有子标签写在同一行.

（2）父元素设置font-size：0，在子元素上重置正确的font-size.

（3）将子元素设置为float：left.

## 7、em\px\rem区别（vh、vw）

**px**:绝对单位，页面按精确像素展示。

**em**:相对单位，基准点为父节点字体的大小，如果自身定义了font-size按自身来计算（浏览器默认字体是16px），整个页面内1em不是一个固定的值。

**rem**:相对单位，可理解为”root em”, 相对根节点html的字体大小来计算，CSS3新加属性。

**vh**:视窗高度的百分比。

**vw**:视窗宽度的百分比（1vw 代表视窗的宽度为 1%）。

**补充**：

vmin：取当前Vw和Vh中较小的那一个值。
vmax：取当前Vw和Vh中较大的那一个值。

## 8、rem布局的原理解析

**其实rem布局的本质是等比缩放**

## 9、BFC

### 1、什么是BFC

**Block Fromatting Context （块级格式上下文）**

**哪些会为他们的内容创建新的BFC（触发条件详细介绍）**：（1）浮动元素和绝对定位元素（2）非块级盒子的块级容器（例如 inlineblocks，table-cells，和table-captions）（3）overflow值不为“visible”的块级盒子

**它的作用是在一块独立的区域，让处于BFC内部的元素与外部的元素互相隔离**

### 2、触发条件

（1）根元素

（2）浮动元素（元素的 float 不是 none）

（3）绝对定位元素（元素的 position 为 absolute 或 fixed）

（4）行内块元素（元素的 display 为 inline-block）

（5）表格单元格（元素的 display为 table-cell，HTML表格单元格默认为该值）

（6）表格标题（元素的 display 为 table-caption，HTML表格标题默认为该值）

（7）匿名表格单元格元素（元素的 display为 table、table-row、 table-row-group、table-header-group、table-footer-group（分别是HTML table、row、tbody、thead、tfoot的默认属性）或 inline-table）

（8）overflow 值不为 visible 的块元素 -弹性元素（display为 flex 或 inline-flex元素的直接子元素）

（9）网格元素（display为 grid 或 inline-grid 元素的直接子元素） 等等

### 3、BFC渲染规则

（1）BFC垂直方向边距重叠

（2）BFC的区域不会与浮动元素的box重叠

（3）BFC是一个独立的容器，外面的元素不会影响里面的元素

（4）计算BFC高度的时候浮动元素也会参与计算

### 4、应用场景

（1）防止浮动导致父元素高度塌陷

## 10、你对flex的理解

建议看阮大神的文章，我学习的时候还是总结了一篇脑图想看就移步 [flex布局脑图总结](https://juejin.cn/post/6897785503202934791)

## 11、如何理解z-index

1、控制重叠元素的垂直叠加顺序。

2、默认元素的z-index为0。

3、我们可以修改z-index来控制元素的图层位置。

4、而且z-index只能影响设置了position值的元素。

## 12、如何理解层叠上下文

### 1、什么是层叠上下文

（1）层叠上下文是HTML元素的三维概念

（2）这些HTML元素在一条假想的相对于面向（电脑屏幕的）视窗或者网页的用户的z轴上延伸

（3）HTML元素依据其自身属性按照优先级顺序占用层叠上下文的空间

### 2、如何产生

（1）根元素 (HTML)

（2）z-index 值不为 "auto"的 绝对/相对定位

（2）一个 z-index 值不为 "auto"的 flex 项目 (flex item)，即：父元素 display: flex|inline-flex

（3）opacity 属性值小于 1 的元素（参考 the specification for opacity）

（4）transform 属性值不为 "none"的元素

（5）mix-blend-mode 属性值不为 "normal"的元素

（6）filter值不为“none”的元素

（7）perspective值不为“none”的元素

（8）isolation 属性被设置为 "isolate"的元素

（9）position: fixed

（10）在 will-change 中指定了任意 CSS 属性，即便你没有直接指定这些属性的值

（11）-webkit-overflow-scrolling 属性被设置 "touch"的元素

## 13、浮动布局

### 1、含义

（1）元素浮动后可以向左或向右移动，直到它的边缘碰到包含它的框或者另外一个浮动元素的边框为止

（2）元素浮动以后脱离正常的文档流

### 2、优点

（1）元素浮动起来之后，它有着块级元素的一些性质例如设置宽和高

（2）但它与inline-block还是有一些区别：1、横向排序的适合，float可以设置方向而inline-block方向是固定的。2、inline-block在使用的时候有空白间隙。

### 3、缺点

最明显的缺点就是浮动元素一旦脱离文档流，就无法撑起父元素，会照成父级元素高度塌陷。

### 4、清除浮动

（1）添加额外标签：添加一个额外的标签并添加属性 clear：both（添加了无意义标签，语义化差）。

（2）父级添加overflow属性：通过触发BFC方式实现清除浮动（内容增多的时候容易照成不会自动换行导致内容被隐藏掉，无法显示要益处的元素）。

（3）建立伪元素选择器清除浮动（推荐使用），使用after伪元素清除浮动。

## 14、你对css sprites的理解，好处是什么

### 1、是什么

（1）你对css sprites的理解，好处是什么

（2）开发人员往往将小图标合并在一起之后的图片称作雪碧图

### 2、如何操作

（1）使用工具（PS之类的）将多张图片打包成一张雪碧图，并为其生成合适的 CSS

（2）每张图片都有相应的 CSS 类，该类定义了background-image、background-position和background-size属性。 使用图片时，将相应的类添加到你的元素中

### 3、优点

（1）减少加载多张图片的 HTTP 请求数（感觉在http2.0之后可以说没什么用了）

（2）提前加载资源

### 4、缺点

（1）CSS Sprite维护成本较高，如果页面背景有少许改动，一般就要改这张合并的图片

（2）加载速度优势在http2开启后荡然无存，HTTP2多路复用，多张图片也可以重复利用一个连接通道搞定

## 15、你对媒体查询的理解

### 1、是什么

（1）媒体查询由一个可选的媒体类型和零个或多个使用媒体功能的限制了样式表范围的表达式组成

（2）添加自CSS3，允许内容的呈现针对一个特定范围的输出设备而进行裁剪，而不必改变内容本身,非常适合web网页应对不同型号的设备而做出对应的响应适配

### 2、如何使用

（1）媒体查询包含一个可选的媒体类型和，满足CSS3规范的条件下，包含零个或多个表达式

（2）这些表达式描述了媒体特征，最终会被解析为true或false

（3）如果媒体查询中指定的媒体类型匹配展示文档所使用的设备类型，并且所有的表达式的值都是true，那么该媒体查询的结果为true.那么媒体查询内的样式将会生效

### 3、例子

如果文档宽度小于 300 像素则修改背景颜色(background-color):

```css
@media screen and (max-width: 300px) {
    body {
        background-color:lightblue;
    }
}
```

## 16、你对盒模型的理解

（1）当对一个文档进行布局（lay out）的时候，浏览器的渲染引擎会根据标准之一的 CSS 基础框盒模型（CSS basic box model），将所有元素表示为一个个矩形的盒子（box）

（2）CSS 决定这些盒子的大小、位置以及属性（例如颜色、背景、边框尺寸…）

（3）盒模型由content（内容）、padding（内边距）、border（边框）、margin（外边距）组成

## 17、标准盒模型和怪异盒模型的区别

在W3C标准下，我们定义元素的width值即为盒模型中的content的宽度值，height值即为盒模型中的content的高度值。

### 1、标准盒模型

元素的宽度 = margin-left + border-left + padding-left + width + padding-right + border-right + margin-right（width+padding+border+margin）

### 2、怪异盒模型

元素占据的宽度 = margin-left + width + margin-right（margin+width）

width = border+padding+content   （border和padding包括左右）

### 3、box-sizing

请看下面第18点

## 18、box-sizing有哪些属性

box-sizing: content-box // 标准盒模型(默认)

box-sizing: border-box // 怪异盒模型

box-sizing: padding-box // 火狐的私有模型，没人用

box-sizing:inherit //规定从父元素继承box-sizing属性的值

## 19、为什么有时候人们用translate来改变位置而不是定位

（1）translate()是transform的一个值

（2）改变transform或opacity不会触发浏览器重新布局（reflow）或重绘（repaint），只会触发复合（compositions）

（3）而改变绝对定位会触发重新布局，进而触发重绘和复合。

（4）transform使浏览器为元素创建一个 GPU 图层，但改变绝对定位会使用到 CPU。

（5）因此translate()更高效，可以缩短平滑动画的绘制时间。

（6）而translate改变位置时，元素依然会占据其原始空间，绝对定位就不会发生这种情况 。

## 20、关于CSS的动画与过渡问题

## 21、css中哪些属性会脱离文档流

1、浮动（float）

2、绝对定位（absolute）

3、固定定位（fix）

## 22、CSS有几种定位方式

1、static：正常文档流定位，此时 top, right, bottom, left 和 z-index 属性无效，块级元素从上往下纵向排布，行级元素从左向右排列

2、relative：相对定位，此时的『相对』是相对于正常文档流的位置

3、absolute：相对于最近的非 static 定位祖先元素的偏移，来确定元素位置，比如一个绝对定位元素它的父级、和祖父级元素都为relative，它会相对他的父级而产生偏移。

4、fixed：指定元素相对于屏幕视口（viewport）的位置来指定元素位置。元素的位置在屏幕滚动时不会改变，比如那种回到顶部的按钮一般都是用此定位方式

5、sticky：粘性定位，特性近似于relative和fixed的合体，其在实际应用中的近似效果就是IOS通讯录滚动的时候的『顶屁股』

## 23、position

1、absolute：生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。

2、fixed：生成固定定位的元素，相对于浏览器窗口进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。

3、relative：生成相对定位的元素，相对于其正常位置进行定位。因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。

4、sticky：粘性定位，该定位基于用户滚动的位置。它的行为就像 position:relative; 而当页面滚动超出目标区域时，它的表现就像 position:fixed;，它会固定在目标位置。

5、static：默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。

6、inherit：	规定应该从父元素继承 position 属性的值。

7、initial：initial 关键字用于设置 CSS 属性为它的默认值。

## 24、requestAnimationFrame

## 25、background-size:cover和contain的区别

### 1、在no-repeat的情况下

cover:图片宽高比不变,铺满整个容器的宽高,图片多出来的部分会裁掉

contain:图片宽高比不变 ,缩放至图片完全展示出来,所以会有留白区域

### 2、在repeat情况下

cover:图片宽高比不变,铺满整个容器的宽高,图片多出来的部分会裁掉

contain:容器至少有一张完整的图,留白区域则平铺背景图,铺不下的再裁掉

## 26、translation、transform和translate的区别和联系

**transition和transform都是一种动画，translate是transform的一个方法**

### 属性解析

**translate:移动**

 transform的一个方法
          通过 translate() 方法，元素从其当前位置移动，根据给定的 left（x 坐标） 和 top（y 坐标） 		  位置参数：
          用法：transform: translate(50px, 100px);
                -ms-transform: translate(50px,100px);
                -webkit-transform: translate(50px,100px);
                -o-transform: translate(50px,100px);
                -moz-transform: translate(50px,100px);



**transform:变形，改变**

translate(x,y)  平移距离  单位：px / %(仅限x,y轴使用)
rotate(顺时针角度)  旋转角度   单位：deg
scale(x,y)  缩放倍数  单位：无
skew(x,y)  反转角度  单位：deg
matrix(n,n,n,n,n,n)  把所有 2D 转换方法组合在一起  单位：无



CSS3中主要包括 旋转：rotate() 顺时针旋转给定的角度，允许负值 rotate(30deg)
      扭曲：skew() 元素翻转给定的角度,根据给定的水平线（X 轴）和垂直线（Y 轴）参数：			skew(30deg,20deg)
      缩放：scale() 放大或缩小，根据给定的宽度（X 轴）和高度（Y 轴）参数： scale(2,4)
      移动：translate() 平移，传进 x,y值，代表沿x轴和y轴平移的距离
      所有的2D转换方法组合在一起： matrix()  旋转、缩放、移动以及倾斜元素
      matrix(scale.x ,, , scale.y , translate.x, translate.y) 

改变起点位置 transform-origin: bottom left;



**transition: 允许CSS属性值在一定的时间区间内平滑的过渡**

transition(要过渡的属性 花费的时间 运动曲线 何时开始)

要过渡的属性：包括长、宽等等，如果是全部属性，则选择"all"

花费的时间：以"s"为单位，如"0.5s"
运动曲线：默认为ease(慢-快-慢),其他属性还包括linear(匀速)、ease-in（慢-快）、ease-out（快-慢）ease-in-out(慢-快-慢)
何时开始：以"s"为单位，如"0.5s"



需要事件的触发，例如单击、获取焦点、失去焦点等
      transition:property duration timing-function delay;
     property:CSS的属性，例如：width height 为none时停止所有的运动，可以为transform
     duration:持续时间
     timing-function:ease等
    delay:延迟
    注意：当property为all的时候所有动画
            例如：transition:width 2s ease 0s;

## 27、实现一个三角形  实现一个扇形

```css
 height: 0;
      width: 0;
         border-width: 50px;
         border-style: solid;
         border-color:  transparent #ff0 transparent transparent;
```

三角形的基础上加上一个border-radius: 50%;变成扇形

## 28、水平居中

1、行内元素

```css
text-align：center
```

2、块级元素

**确定宽度**：

```css
margin：0  auto
绝对定位和margin-left：width/2  ///前提：父元素postion：relative
```

**未知宽度**：

```css
1、display：table；margin：0 auto
2、display：inline-block和text-align：center
3、display：flex；justify-conten：center
4、绝对定位+transform，translateX可以移动本身元素的50%
```

## 29、垂直居中

1、利用line-height实现居中（这种方法适合纯文字类，若元素是单行文本, 则可设置 line-height 等于父元素高度）

2、子元素margin为auto：前提：父容器“相对定位”，子级设置绝对定位

3、子元素margin为auto：前提：父级设置display：flex

4、绝对定位+transform，translateY可以移动本身元素的50%：前提：父元素position：relative

5、设置‘vertical-align：middle‘：前提：内联元素以及display为table-cell

## 30、CSS进行圣杯布局（三列布局）

1、利用flex布局

```css
    .container{
        display: flex;
    }
    .middle{
        flex: 1;
        background:yellow;
    }
    .left{
        width:200px;
        background:pink;
    }
    .right{
        background: aqua;
        width:300px;
    }
```

flex布局，中间flex:1(flex-grow：设置为1，中间剩余部分放大1)   flex：默认为0，1，auto。

2、float全局（全部float：left）。

3、float布局（左边float：left，右变float：right）。

4、绝对定位

```css
    .container>div {
      position: absolute;
    }

    .middle {
      left: 200px;
      right: 250px;
      background: yellow;
    }

    .left {
      left: 0;
      width: 200px;
      background: pink;
    }

    .right {
      right: 0;
      width: 250px;
      background: aqua;
    }
```

绝对定位，中间不设置宽度，其余的绝对定位到两边。

5、grid布局

## 31、CSS进行品字布局

```css
div1：margin: 100px auto 0;     
div2:   margin-left: 50%;transform: translateX(-100%);  float: left;
div3:   float: left;transform: translateX(-100%);
```

```css
div1:  margin: 0 auto 0;
div2与div3：  float: left;
        width: 50%;
```

## 32、两列布局

1、左列定宽，右列自适应

（1）后者也适用于前者：左侧float之后，右侧设置margin为左侧宽度。

（2）absolute+定位：需要注意的是父级元素需要设置display: relative。需要注意的是父级元素需要设置display: relative。

2、左列不定宽，右列自适应

（1）float + BFC：左侧float，右侧直接触发BFC，比如overflow：hidden。

（2）table布局：不常用

（3）flex

```css
<div class="parent">
	<div class="left">
		<p>left</p>
	</div>
	<div class="right">
		<p>right</p>
		<p>right</p>
	</div>
</div>
```

```css
.parent{
	display: flex;
}
.left{
	margin-right: 20px;
}
.right{
	flex: 1;
}
.left p{width: 200px;}
```

```css
flew：grow为1之后剩余空间直接占满
```

后者也适用于前者

## 33、div垂直居中，左右10px，高度始终为宽度一半

1、flew：grow为1之后剩余空间直接占满。

2、利用calc和vw：

```css
       /* vw是视口的宽度， 1vw代表1%的视口宽度 */
        width: calc(100vw - 20px);
        /* 宽度的一半 */
        height: calc(50vw - 10px);
```

