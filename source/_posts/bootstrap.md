title: bootstrap

tags: 

- 开发
- bootstrap

categories:

- 前端

type:

- picture

description: <center><h4>将以后学习开发的大概流程记录下来…</h4></center>

photo:  

- https://biaofendou.github.io/images/photos/backgroud.jpg

---

<!-- more -->

---

# bootstrap简介

<div style="margin:0 auto;">
    <div style="position:absolute;">
        <img src='https://www.runoob.com/wp-content/uploads/2013/10/bs.png' width='100%' height='100%' >
    </div>
<div style="margin-left:200px;">
     <h3>
          &nbsp;&nbsp;Bootstrap，来自 Twitter，是目前最受欢迎的前端框架。Bootstrap 是基于 HTML、CSS、JAVASCRIPT 的，它简洁灵活，使得 Web 开发更加快捷。
    </h3>
    </div>
</div>



## bootstrap优点

- **移动设备优先**：自 Bootstrap 3 起，框架包含了贯穿于整个库的移动设备优先的样式。

- **浏览器支持**：所有的主流浏览器都支持 Bootstrap。

- **容易上手**：只要您具备 HTML 和 CSS 的基础知识，您就可以开始学习 Bootstrap。

- **响应式设计**：Bootstrap 的响应式 CSS 能够自适应于台式机、平板电脑和手机。更多有关响应式设计的内容详见 [Bootstrap 响应式设计](https://www.runoob.com/bootstrap/bootstrap-v2-responsive-design.html)。

  ![](https://www.runoob.com/wp-content/uploads/2014/06/responsive.jpg)

## Bootstrap 包的内容

- **基本结构**：Bootstrap 提供了一个带有网格系统、链接样式、背景的基本结构。

- **CSS**：Bootstrap 自带以下特性：全局的 CSS 设置、定义基本的 HTML 元素样式、可扩展的 class，以及一个先进的网格系统。

- **组件**：Bootstrap 包含了十几个可重用的组件，用于创建图像、下拉菜单、导航、警告框、弹出框等等。

- **JavaScript 插件**:Bootstrap 包含了十几个自定义的 jQuery 插件。您可以直接包含所有的插件，也可以逐个包含这些插件。

- **定制**：您可以定制 Bootstrap 的组件、LESS 变量和 jQuery 插件来得到您自己的版本。

  

## bootstrap安装

[官网地址](https://getbootstrap.com/ )

[下载地址](https://getbootstrap.com/docs/4.3/getting-started/download/)

- *Download Bootstrap*：下载 Bootstrap。点击该按钮，您可以下载 Bootstrap CSS、JavaScript 和字体的预编译的压缩版本。不包含文档和最初的源代码文件。
- *Download Source*：下载源代码。点击该按钮，您可以直接从 from 上得到最新的 Bootstrap LESS 和 JavaScript 源代码。

## 文件结构

### 预编译的 Bootstrap

当您下载了 Bootstrap 的已编译的版本，解压缩 ZIP 文件，您将看到下面的文件/目录结构：

![结构地址](https://www.runoob.com/wp-content/uploads/2014/06/compiledfilestructure.jpg)

如上图所示，可以看到已编译的 CSS 和 JS（bootstrap.*），以及已编译压缩的 CSS 和 JS（bootstrap.min.*）。同时也包含了 Glyphicons 的字体，这是一个可选的 Bootstrap 主题。

### Bootstrap 源代码

如果您下载了 Bootstrap 源代码，那么文件结构将如下所示：

![源代码](https://www.runoob.com/wp-content/uploads/2014/06/sourcecodefilestructure.jpg)

- *less/*、*js/* 和 *fonts/* 下的文件分别是 Bootstrap CSS、JS 和图标字体的源代码。
- *dist/* 文件夹包含了上面预编译下载部分中所列的文件和文件夹。
- *docs-assets/*、*examples/* 和所有的 **.html* 文件是 Bootstrap 文档。



# bootstrap CSS

## bootstrap 特点

### 移动设备优先

移动设备优先是 Bootstrap 3 的最显著的变化。

在之前的 Bootstrap 版本中（直到 2.x），您需要手动引用另一个 CSS，才能让整个项目友好的支持移动设备。

现在不一样了，Bootstrap 3 默认的 CSS 本身就对移动设备友好支持。

Bootstrap 3 的设计目标是移动设备优先，然后才是桌面设备。这实际上是一个非常及时的转变，因为现在越来越多的用户使用移动设备。

为了让 Bootstrap 开发的网站对移动设备友好，确保适当的绘制和触屏缩放，需要在网页的 head 之中添加 **viewport meta** 标签，如下所示：

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

*width* 属性控制设备的宽度。假设您的网站将被带有不同屏幕分辨率的设备浏览，那么将它设置为 *device-width* 可以确保它能正确呈现在不同设备上。

*initial-scale=1.0* 确保网页加载时，以 1:1 的比例呈现，不会有任何的缩放。

在移动设备浏览器上，通过为 **viewport meta** 标签添加 *user-scalable=no* 可以禁用其缩放（zooming）功能。

通常情况下，*maximum-scale=1.0* 与 user-scalable=no 一起使用。这样禁用缩放功能后，用户只能滚动屏幕，就能让您的网站看上去更像原生应用的感觉。

注意，这种方式我们并不推荐所有网站使用，还是要看您自己的情况而定！

```html
<meta name="viewport" content="width=device-width, 
                                     initial-scale=1.0, 
                                     maximum-scale=1.0, 
                                     user-scalable=no">
```

### 响应式图像

```html
<img src="..." class="img-responsive" alt="响应式图像">
```

通过添加 *img-responsive* class 可以让 Bootstrap 3 中的图像对响应式布局的支持更友好。

接下来让我们看下这个 class 包含了哪些 css 属性。

在下面的代码中，可以看到*img-responsive* class 为图像赋予了 max-width: 100%; 和 height: auto; 属性，可以让图像按比例缩放，不超过其父元素的尺寸。

```html
.img-responsive {
  display: block;
  height: auto;
  max-width: 100%;
}
```

这表明相关的图像呈现为 *block*。当您把元素的 display 属性设置为 block，以块级元素显示。

设置 *height:auto*，相关元素的高度取决于浏览器。

设置 *max-width* 为 100% 会重写任何通过 width 属性指定的宽度。这让图片对响应式布局的支持更友好。

如果需要让使用了 .img-responsive 类的图片水平居中，请使用 .center-block 类，不要用 .text-center。

### 全局显示、排版和链接

#### 基本的全局显示

Bootstrap 3 使用 *body {margin: 0;}* 来移除 body 的边距。

请看下面有关 body 的设置：

```html
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 14px;
  line-height: 1.428571429;
  color: #333333;
  background-color: #ffffff;
}
```

一条规则设置 body 的默认字体样式为 *"Helvetica Neue", Helvetica, Arial, sans-serif*。

第二条规则设置文本的默认字体大小为 14 像素。

第三条规则设置默认的行高度为 1.428571429。

第四条规则设置默认的文本颜色为 #333333。

最后一条规则设置默认的背景颜色为白色。

#### 排版

使用 @font-family-base、 @font-size-base 和 @line-height-base 属性作为排版样式。

#### 链接样式

通过属性 @link-color 设置全局链接的颜色。

对于链接的默认样式，如下设置：

```html
a:hover,
a:focus {
  color: #2a6496;
  text-decoration: underline;
}

a:focus {
  outline: thin dotted #333;
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
```

所以，当鼠标悬停在链接上，或者点击过的链接，颜色会被设置为 #2a6496。同时，会呈现一条下划线。

除此之外，点击过的链接，会呈现一个颜色码为 #333 的细的虚线轮廓。另一条规则是设置轮廓为 5 像素宽，且对于基于 webkit 浏览器有一个 *-webkit-focus-ring-color* 的浏览器扩展。轮廓偏移设置为 -2 像素。

以上所有这些样式都可以在 scaffolding.less 中找到。

### 避免跨浏览器的不一致

Bootstrap 使用 [Normalize](http://necolas.github.io/normalize.css/) 来建立跨浏览器的一致性。

Normalize.css 是一个很小的 CSS 文件，在 HTML 元素的默认样式中提供了更好的跨浏览器一致性。

### 容器（Container）

```html
<div class="container">
  ...
</div>
```

Bootstrap 3 的 *container* class 用于包裹页面上的内容。让我们一起来看看 bootstrap.css 文件中的这个 *.container* class。

```html
.container {
   padding-right: 15px;
   padding-left: 15px;
   margin-right: auto;
   margin-left: auto;
}
```

通过上面的代码，把 container 的左右外边距（margin-right、margin-left）交由浏览器决定。

请注意，由于内边距（padding）是固定宽度，默认情况下容器是不可嵌套的。

```html
.container:before,
.container:after {
  display: table;
  content: " ";
}
```

这会产生伪元素。设置 *display* 为 *table*，会创建一个匿名的 table-cell 和一个新的块格式化上下文。*:before* 伪元素防止上边距崩塌，*:after* 伪元素清除浮动。

如果 *conteneditable* 属性出现在 HTML 中，由于一些 Opera bug，围绕上述元素创建一个空格。这可以通过使用 *content: " "* 来修复。

```html
.container:after {
  clear: both;
}
```

它创建了一个伪元素，并确保了所有的容器包含所有的浮动元素。

Bootstrap 3 CSS 有一个申请响应的媒体查询，在不同的媒体查询阈值范围内都为 container 设置了max-width，用以匹配网格系统。

```html
@media (min-width: 768px) {
   .container {
      width: 750px;
}
```

### Bootstrap 浏览器/设备支持

Bootstrap 可以在最新的桌面系统和移动端浏览器中很好的工作。

旧的浏览器可能无法很好的支持。

下表为 Bootstrap 支持最新版本的浏览器和平台：

|              | Chrome | Firefox | IE     | Opera  | Safari |
| :----------- | :----- | :-----: | :----- | :----- | :----: |
| **Android**  | YES    | YES     | 不适用 | 不适用 | 不适用 |
| **iOS**      | YES    | 不适用  | 不适用 | 不适用 |  YES   |
| **Mac OS X** | YES    | YES     | 不适用 | YES    |  YES   |
| **Windows**  | YES    | YES     | YES | YES    | 不适用 |

> Bootstrap 支持 Internet Explorer 8 及更高版本的 IE 浏览器。

## Bootstrap 网格系统（Grid System）

Bootstrap 提供了一套响应式、移动设备优先的流式网格系统，随着屏幕或视口（viewport）尺寸的增加，系统会自动分为最多12列。

### 什么是网格（Grid）？

摘自维基百科：

> 在平面设计中，网格是一种由一系列用于组织内容的相交的直线（垂直的、水平的）组成的结构（通常是二维的）。它广泛应用于打印设计中的设计布局和内容结构。在网页设计中，它是一种用于快速创建一致的布局和有效地使用 HTML 和 CSS 的方法。

简单地说，网页设计中的网格用于组织内容，让网站易于浏览，并降低用户端的负载。

### 什么是 Bootstrap 网格系统（Grid System）？

Bootstrap 官方文档中有关网格系统的描述：

> Bootstrap 包含了一个响应式的、移动设备优先的、不固定的网格系统，可以随着设备或视口大小的增加而适当地扩展到 12 列。它包含了用于简单的布局选项的预定义类，也包含了用于生成更多语义布局的功能强大的混合类。

让我们来理解一下上面的语句。Bootstrap 3 是移动设备优先的，在这个意义上，Bootstrap 代码从小屏幕设备（比如移动设备、平板电脑）开始，然后扩展到大屏幕设备（比如笔记本电脑、台式电脑）上的组件和网格。

### 移动设备优先策略

- 内容
  - 决定什么是最重要的。
- 布局
  - 优先设计更小的宽度。
  - 基础的 CSS 是移动设备优先，媒体查询是针对于平板电脑、台式电脑。
- 渐进增强
  - 随着屏幕大小的增加而添加元素。

响应式网格系统随着屏幕或视口（viewport）尺寸的增加，系统会自动分为最多12列。

<table border=0 cellpadding=0 cellspacing=0 width=768 style='border-collapse:
 collapse;table-layout:fixed;width:576pt'>
 <col width=64 span=12 style='width:48pt'>
 <tr height=18 style='height:13.8pt'>
  <td height=18 class=xl6317677 width=64 style='height:13.8pt;width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
  <td class=xl6317677 width=64 style='width:48pt'>1</td>
 </tr>
 <tr height=18 style='height:13.8pt'>
  <td colspan=4 height=18 class=xl6317677 style='height:13.8pt'>4</td>
  <td colspan=4 class=xl6317677>4</td>
  <td colspan=4 class=xl6317677>4</td>
 </tr>
 <tr height=18 style='height:13.8pt'>
  <td colspan=4 height=18 class=xl6317677 style='height:13.8pt'>4</td>
  <td colspan=8 class=xl6317677>8</td>
 </tr>
 <tr height=18 style='height:13.8pt'>
  <td colspan=6 height=18 class=xl6317677 style='height:13.8pt'>6</td>
  <td colspan=6 class=xl6317677>6</td>
 </tr>
 <tr height=18 style='height:13.8pt'>
  <td colspan=12 height=18 class=xl6317677 style='height:13.8pt'>12</td>
 </tr>
</table>

### Bootstrap 网格系统（Grid System）的工作原理

网格系统通过一系列包含内容的行和列来创建页面布局。下面列出了 Bootstrap 网格系统是如何工作的：

- 行必须放置在 **.container** class 内，以便获得适当的对齐（alignment）和内边距（padding）。
- 使用行来创建列的水平组。
- 内容应该放置在列内，且唯有列可以是行的直接子元素。
- 预定义的网格类，比如 **.row** 和 **.col-xs-4**，可用于快速创建网格布局。LESS 混合类可用于更多语义布局。
- 列通过内边距（padding）来创建列内容之间的间隙。该内边距是通过 **.rows** 上的外边距（margin）取负，表示第一列和最后一列的行偏移。
- 网格系统是通过指定您想要横跨的十二个可用的列来创建的。例如，要创建三个相等的列，则使用三个 **.col-xs-4**。

### 媒体查询

媒体查询是非常别致的"有条件的 CSS 规则"。它只适用于一些基于某些规定条件的 CSS。如果满足那些条件，则应用相应的样式。

Bootstrap 中的媒体查询允许您基于视口大小移动、显示并隐藏内容。下面的媒体查询在 LESS 文件中使用，用来创建 Bootstrap 网格系统中的关键的分界点阈值。

```html
/* 超小设备（手机，小于 768px） */
/* Bootstrap 中默认情况下没有媒体查询 */

/* 小型设备（平板电脑，768px 起） */
@media (min-width: @screen-sm-min) { ... }

/* 中型设备（台式电脑，992px 起） */
@media (min-width: @screen-md-min) { ... }

/* 大型设备（大台式电脑，1200px 起） */
@media (min-width: @screen-lg-min) { ... }
```

我们有时候也会在媒体查询代码中包含 **max-width**，从而将 CSS 的影响限制在更小范围的屏幕大小之内。

```html
@media (max-width: @screen-xs-max) { ... }
@media (min-width: @screen-sm-min) and (max-width: @screen-sm-max) { ... }
@media (min-width: @screen-md-min) and (max-width: @screen-md-max) { ... }
@media (min-width: @screen-lg-min) { ... }
```

媒体查询有两个部分，先是一个设备规范，然后是一个大小规则。在上面的案例中，设置了下列的规则：

让我们来看下面这行代码：

```html
@media (min-width: @screen-sm-min) and (max-width: @screen-sm-max) { ... }
```

对于所有带有 *min-width: @screen-sm-min* 的设备，如果屏幕的宽度小于 *@screen-sm-max*，则会进行一些处理。

### 网格选项

下表总结了 Bootstrap 网格系统如何跨多个设备工作：

|              | 超小设备手机（<768px）         | 小型设备平板电脑（≥768px）     | 中型设备台式电脑（≥992px）     | 大型设备台式电脑（≥1200px）    |
| :----------- | :----------------------------- | :----------------------------- | :----------------------------- | :----------------------------- |
| 网格行为     | 一直是水平的                   | 以折叠开始，断点以上是水平的   | 以折叠开始，断点以上是水平的   | 以折叠开始，断点以上是水平的   |
| 最大容器宽度 | None (auto)                    | 750px                          | 970px                          | 1170px                         |
| Class 前缀   | **.col-xs-**                   | **.col-sm-**                   | **.col-md-**                   | **.col-lg-**                   |
| 列数量和     | 12                             | 12                             | 12                             | 12                             |
| 最大列宽     | Auto                           | 60px                           | 78px                           | 95px                           |
| 间隙宽度     | 30px （一个列的每边分别 15px） | 30px （一个列的每边分别 15px） | 30px （一个列的每边分别 15px） | 30px （一个列的每边分别 15px） |
| 可嵌套       | Yes                            | Yes                            | Yes                            | Yes                            |
| 偏移量       | Yes                            | Yes                            | Yes                            | Yes                            |
| 列排序       | Yes                            | Yes                            | Yes                            | Yes                            |

### 基本的网格结构

下面是 Bootstrap 网格的基本结构：

```html
<div class="container">
   <div class="row">
      <div class="col-*-*"></div>
      <div class="col-*-*"></div>      
   </div>
   <div class="row">...</div>
</div>
<div class="container">....
```

## Bootstrap 排版

Bootstrap 使用 Helvetica Neue、 Helvetica、 Arial 和 sans-serif 作为其默认的字体栈。

使用 Bootstrap 的排版特性，您可以创建标题、段落、列表及其他内联元素。

### 标题

Bootstrap 中定义了所有的 HTML 标题（h1 到 h6）的样式。请看下面的实例：



```html
<h1>我是标题1 h1</h1>
<h2>我是标题2 h2</h2>
<h3>我是标题3 h3</h3>
<h4>我是标题4 h4</h4>
<h5>我是标题5 h5</h5>
<h6>我是标题6 h6</h6>
```

#### 内联子标题

如果需要向任何标题添加一个内联子标题，只需要简单地在元素两旁添加 <small>，或者添加 **.small** class，这样子您就能得到一个字号更小的颜色更浅的文本，如下面实例所示：

```html
<h1>我是标题1 h1. <small>我是副标题1 h1</small></h1>
<h2>我是标题2 h2. <small>我是副标题2 h2</small></h2>
<h3>我是标题3 h3. <small>我是副标题3 h3</small></h3>
<h4>我是标题4 h4. <small>我是副标题4 h4</small></h4>
<h5>我是标题5 h5. <small>我是副标题5 h5</small></h5>
<h6>我是标题6 h6. <small>我是副标题6 h6</small></h6>
```

#### 引导主体副本

为了给段落添加强调文本，则可以添加 class="lead"，这将得到更大更粗、行高更高的文本，如下面实例所示：


<p class="lead">这是一个演示引导主体副本用法的实例。这是一个演示引导主体副本用法的实例。这是一个演示引导主体副本用法的实例。这是一个演示引导主体副本用法的实例。这是一个演示引导主体副本用法的实例。这是一个演示引导主体副本用法的实例。这是一个演示引导主体副本用法的实例。这是一个演示引导主体副本用法的实例。</p>
### 强调

HTML 的默认强调标签 <small>（设置文本为父文本大小的 85%）、<strong>（设置文本为更粗的文本）、<em>（设置文本为斜体）。

Bootstrap 提供了一些用于强调文本的类，如下面实例所示：

```html
<strong>本行内容是在标签内</strong><br>
<em>本行内容是在标签内，并呈现为斜体</em><br>
<p class="text-left">向左对齐文本</p>
<p class="text-center">居中对齐文本</p>
<p class="text-right">向右对齐文本</p>
<p class="text-muted">本行内容是减弱的</p>
<p class="text-primary">本行内容带有一个 primary class</p>
<p class="text-success">本行内容带有一个 success class</p>
<p class="text-info">本行内容带有一个 info class</p>
<p class="text-warning">本行内容带有一个 warning class</p>
<p class="text-danger">本行内容带有一个 danger class</p>
```

### 缩写

HTML 元素提供了用于缩写的标记，比如 WWW 或 HTTP。Bootstrap 定义 <abbr> 元素的样式为显示在文本底部的一条虚线边框，当鼠标悬停在上面时会显示完整的文本（只要您为 <abbr> title 属性添加了文本）。为了得到一个更小字体的文本，请添加 .initialism 到 <abbr>。

```html
<abbr title="World Wide Web">WWW</abbr><br>
<abbr title="Real Simple Syndication" class="initialism">RSS</abbr>
```

### 地址（Address）

使用 ```**<address>**``` 标签，您可以在网页上显示联系信息。由于``` **<address>**``` 默认为 **display:block;**，您需要使用``` **<br>**``` 标签来为封闭的地址文本添加换行。

```
 <address>
 <strong>Some Company, Inc.</strong><br>
  007 street<br>
  Some City, State XXXXX<br>
  <abbr title="Phone">P:</abbr> (123) 456-7890
</address>
<address>
  <strong>Full Name</strong><br>
  <a href="mailto:#">mailto@somedomain.com</a>
</address>
```

### 引用（Blockquote）

您可以在任意的 HTML 文本旁使用默认的 ```<blockquote>```。其他选项包括，添加一个``` <small>``` 标签来标识引用的来源，使用 class *.pull-right* 向右对齐引用。下面的实例演示了这些特性：

```html
<blockquote>
  <p>
  这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。
  </p>
</blockquote>
<blockquote>
  这是一个带有源标题的引用。
  <small>Someone famous in <cite title="Source Title">Source Title</cite></small>
</blockquote>
<blockquote class="pull-right">
  这是一个向右对齐的引用。
  <small>Someone famous in <cite title="Source Title">Source Title</cite></small>
</blockquote>
```

### 列表

Bootstrap 支持有序列表、无序列表和定义列表。

- **有序列表**：有序列表是指以数字或其他有序字符开头的列表。
- **无序列表**：无序列表是指没有特定顺序的列表，是以传统风格的着重号开头的列表。如果您不想显示这些着重号，您可以使用 class *.list-unstyled* 来移除样式。您也可以通过使用 class *.list-inline* 把所有的列表项放在同一行中。
- **定义列表**：在这种类型的列表中，每个列表项可以包含 ```<dt>``` 和 ```<dd>``` 元素。```<dt> ```代表 *定义术语*，就像字典。接着，```<dd> ```是``` <dt>``` 的描述。`.dl-horizontal` 可以让 `<dl>` 内的短语及其描述排在一行。开始是像 `<dl>` 的默认样式堆叠在一起，随着导航条逐渐展开而排列在一行。

下面的实例演示了这些类型的列表：

```html
<h4>有序列表</h4>
<ol>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
</ol>
<h4>无序列表</h4>
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
</ul>
<h4>未定义样式列表</h4>
<ul class="list-unstyled">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
</ul>
<h4>内联列表</h4>
<ul class="list-inline">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
</ul>
<h4>定义列表</h4>
<dl>
  <dt>Description 1</dt>
  <dd>Item 1</dd>
  <dt>Description 2</dt>
  <dd>Item 2</dd>
</dl>
<h4>水平的定义列表</h4>
<dl class="dl-horizontal">
  <dt>Description 1</dt>
  <dd>Item 1</dd>
  <dt>Description 2</dt>
  <dd>Item 2</dd>
</dl>
```

### 更多排版类

下表提供了 Bootstrap 更多排版类的实例：

| 类              | 描述                                        |
| :-------------- | :------------------------------------------ |
| .lead           | 使段落突出显示                              |
| .small          | 设定小文本 (设置为父文本的 85% 大小)        |
| .text-left      | 设定文本左对齐                              |
| .text-center    | 设定文本居中对齐                            |
| .text-right     | 设定文本右对齐                              |
| .text-justify   | 设定文本对齐,段落中超出屏幕部分文字自动换行 |
| .text-nowrap    | 段落中超出屏幕部分不换行                    |
| .text-lowercase | 设定文本小写                                |
| .text-uppercase | 设定文本大写                                |

# Bootstrap 代码

Bootstrap 允许您以两种方式显示代码：

- 第一种是``` <code>``` 标签。如果您想要内联显示代码，那么您应该使用 ```<code> ```标签。
- 第二种是``` <pre>``` 标签。如果代码需要被显示为一个独立的块元素或者代码有多行，那么您应该使用 ```<pre>``` 标签。

请确保当您使用``` <pre>``` 和 ```<code> ```标签时，开始和结束标签使用了 unicode 变体： **&lt;** 和 **&gt;**。

让我们来看看下面的实例：

```html
<p><code>&lt;header&gt;</code> 作为内联元素被包围。</p>
<p>如果需要把代码显示为一个独立的块元素，请使用 &lt;pre&gt; 标签：</p>
<pre>
    &lt;article&gt;
        &lt;h1&gt;Article Heading&lt;/h1&gt;
    &lt;/article&gt;
</pre>
```

<p><code>&lt;header&gt;</code> 作为内联元素被包围。</p>
<p>如果需要把代码显示为一个独立的块元素，请使用 &lt;pre&gt; 标签：</p>
<pre>
    &lt;article&gt;
        &lt;h1&gt;Article Heading&lt;/h1&gt;
    &lt;/article&gt;
</pre>

## 更多实例

| 元素/类                      | 描述                         |
| :--------------------------- | :--------------------------- |
| ``` <var> ```                       | 变量赋值: x = ab + y         |
| ```<kbd>```                       | 按键提示： CTRL + P          |
| ```<pre>```                        | 多行代码                     |
| ```<pre class="pre-scrollable"> ```| 多行代码带有滚动条           |
|``` <samp> ```                      | 电脑程序输出: Sample output  |
| ```<code> ```                     | 同一行代码片段: `span`, `div |



# Bootstrap 表格

Bootstrap 提供了一个清晰的创建表格的布局。下表列出了 Bootstrap 支持的一些表格元素：

| 标签      | 描述                                                         |
| :-------- | :----------------------------------------------------------- |
| ```<table>```   | 为表格添加基础样式。                                         |
|``` <thead>```   | 表格标题行的容器元素（	```<tr>```），用来标识表格列。               |
|``` <tbody> ```  | 表格主体中的表格行的容器元素（```<tr>```）。                       |
| ```<tr>   ```   | 一组出现在单行上的表格单元格的容器元素（```<td>``` 或 ```<th>```）。     |
| ```<td>    ```  | 默认的表格单元格。                                           |
| ```<th> ```     | 特殊的表格单元格，用来标识列或行（取决于范围和位置）。必须在 ```<thead>``` 内使用。 |
| ```<caption>``` | 关于表格存储内容的描述或总结。                               |

### 表格类

下表样式可用于表格中：

| 类                   | 描述                                            |
| :------------------- | :---------------------------------------------- |
| .table               | 为任意 ```<table>``` 添加基本样式 (只有横向分隔线)    |
| .table-striped       | 在 ```<tbody> ```内添加斑马线形式的条纹 ( IE8 不支持) |
| .table-bordered      | 为所有表格的单元格添加边框                      |
| .table-hover         | 在 ```<tbody>``` 内的任一行启用鼠标悬停状态           |
| .table-condensed     | 让表格更加紧凑                                  |
| *联合使用所有表格类* |                                                 |