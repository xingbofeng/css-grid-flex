# 轴线与网格

`轴线与网格`这篇文章着重于介绍`grid`与`flex`布局的由来，以及一些初级的储备知识。

### 容器的声明
任何容器，我们均可以将它指定为`flex`布局方式或`grid`布局方式。
我们通过`display: flex;`或`display: grid;`，将容器声明为弹性盒子布局或网格布局方式。

行内元素同样可以使用`flex`布局方式或`grid`布局方式。

我们通过`display: inline-flex;`或`display: inline-grid;`声明行内元素的弹性盒子布局或网格布局方式。

### flex与grid的轴线与网格
#### flex的轴线

采用`flex`布局的元素，称为`flex容器（flex container）`。它的所有子元素自动成为容器成员，称为`flex项目（flex item）`。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-2.png)

容器默认存在两根轴：水平的`主轴（main axis）`和垂直的`交叉轴（cross axis）`。主轴的开始位置（与边框的交叉点）叫做`main start`，结束位置叫做`main end`；交叉轴的开始位置叫做`cross start`，结束位置叫做`cross end`。
项目默认沿主轴排列。单个项目占据的主轴空间叫做`main size`，占据的交叉轴空间叫做`cross size`。
#### grid的网格线与网格
类似于`flex`布局方式，`grid`布局中最基本的单位就是网格线与网格了。

采用`grid`布局的元素，称为`grid容器（grid container）`。它的所有子元素自动成为容器成员，称为`grid项目（grid item）`。

分隔的线组成了网格的结构。它们可以是垂直的（“列网格线”）或者水平的（“行网格线”），也可以在行或列的任一边。下面的例子中黄色的线是一个列网格线的例子。

##### 网格线
每条网格线具有默认的编号，从左到右和从上到下分别为1,2,3......

![image](http://oczira72b.bkt.clouddn.com/grid-flex-3.jpg)

##### 网格单元

网格单元是指两根毗邻的行网格线和列网格线中间的位置，它是一个单独的网格“单元”，如图所示，网格单元是指第 1 和 2 根行网格线和第 2 和 3 根列网格线中间的位置。

![image](http://oczira72b.bkt.clouddn.com/flex-grid-4.png)

##### 网格轨迹

网格轨迹是指两根毗邻线中间的位置，你可以认为是网格的行或者列，下面例子的中网格轨迹是第二和第三行网格线中间的位置。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-26.png)

##### 网格区域

网格区域是指 4 根网格线包围的空间，一个网格空间可能由任意数量的网格单元构成。下面的例子中网格区域是指在第 1 和 3 的行网格线和第 1 和 3 列网格线中间的位置。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-27.png)

有了这些基本概念，我们能更好的地理解`flex`与`gird`布局了。

参考资料：

* [flex布局教程](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
* [A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)