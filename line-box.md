# 轴线与网格

最近在深入研究CSS的布局方式的过程中的一些总结。主要是对于CSS3标准里的`flex`布局方式CSS4草案中的`grid`布局方式进行一些总结。

由于内容还是蛮多的，所以分成几篇文章归纳。

而**grid与flex介绍（轴线与网格）**这篇文章着重于介绍`grid`与`flex`布局的由来，以及一些初级的储备知识。

<!--more-->
### 为什么想写这系列的博文？
现今的前端开发中，页面布局主要以基于盒模型的布局方式，也就是常说的`div`+`css`。
我们通过`display`、`float`、`position`布局页面。

传统页面布局过于繁琐，代码冗余，一些功能不易于简单实现：例如垂直居中、等分宽高等。
### 为什么是“拥抱未来”？
`flex`布局又称`弹性盒子`布局，它于2009年提出，并已经进入CSS3标准。现今虽已得到众高端浏览器厂商的支持，但由于IE10以下的用户基数仍然很大，大部分Web开发者并不能够真正在某种程度上大胆尝试这种新型布局理念。

而`grid`布局则更加新奇了，甚至说到今天，连chrome这样的现代化浏览器都没有支持它。

那为什么要谈它呢？

`grid`布局是2010年由`Microsoft`提出的，**目前已经成为W3C候选标准**。虽然说我们依旧不能够通过正常方式使用这样的布局方式，但我们还是通过浏览器的设置可以看到相关的效果。比如Chrome浏览器中通过`chrome://flags`打开Chrome浏览器实验网络平台功能。，将`experimental web platform features`选项设置为`enable`，这个方法同样适用于 Opera，对于Oprea来说，地址为`opera://flags`。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-1.jpg)

打开后，我们将能够在浏览器中正常使用`grid`的布局方式了。

若要在项目当中使用`grid`布局方式，则可能需要安装[css-grid-polyfill](https://github.com/FremyCompany/css-grid-polyfill)。

### 容器的声明
任何容器，我们均可以将它指定为`flex`布局方式或`grid`布局方式。
我们通过`display: flex;`或`display: grid;`，将容器声明为弹性盒子布局或网格布局方式。

行内元素同样可以使用`flex`布局方式或`grid`布局方式。

我们通过`display: inline-flex;`或`display: inline-grid;`声明行内元素的弹性盒子布局或网格布局方式。

### flex与grid的轴线与网格
#### flex的轴线
以下内容参考至阮一峰老师的[flex布局教程](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)：

采用`flex`布局的元素，称为**flex容器（flex container）**。它的所有子元素自动成为容器成员，称为**flex项目（flex item）**。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-2.png)

容器默认存在两根轴：水平的**主轴（main axis）**和垂直的**交叉轴（cross axis）**。主轴的开始位置（与边框的交叉点）叫做**main start**，结束位置叫做**main end**；交叉轴的开始位置叫做**cross start**，结束位置叫做**cross end**。
项目默认沿主轴排列。单个项目占据的主轴空间叫做**main size**，占据的交叉轴空间叫做**cross size**。
#### grid的网格线与网格
类似于`flex`布局方式，`grid`布局中最基本的单位就是网格线与网格了。

采用`grid`布局的元素，称为**grid容器（grid container）**。它的所有子元素自动成为容器成员，称为**grid项目（grid item）**。

分隔的线组成了网格的结构。它们可以是垂直的（“列网格线”）或者水平的（“行网格线”），也可以在行或列的任一边。下面的例子中黄色的线是一个列网格线的例子。

每条网格线具有默认的编号，从左到右和从上到下分别为1,2,3......
![image](http://oczira72b.bkt.clouddn.com/grid-flex-3.jpg)

网格单元是指两根毗邻的行网格线和列网格线中间的位置，它是一个单独的网格“单元”，如图所示，网格单元是指第 1 和 2 根行网格线和第 2 和 3 根列网格线中间的位置。

![image](http://oczira72b.bkt.clouddn.com/flex-grid-4.png)

有了这些基本概念，我们能更好的地理解`flex`与`gird`布局了。
