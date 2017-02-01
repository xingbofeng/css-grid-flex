# grid基础语法介绍(上)

《轴线与网格》里主要讲述了`grid`与`flex`中，网格与轴线的基本概念，了解了这些基本概念之后，我们可以更轻松地对布局方式进行研究，这一篇文章主要描述`grid`布局中，定义在容器的相关属性。

由于我之前也没有真正接触和使用过`grid`，因此接下来的内容算是一些我个人的探索和学习笔记吧，其中部分参考国内外优秀的`grid布局`的相关文献，希望能在我写完、您研究完之后能够真正有所收获。

## 定义在容器的属性
### disaplay
`display`属性定义了一个网格容器，容器是展现为行内或块状由所给定的值而决定，此时，他的所有子元素进入grid文档流，称为grid项目。
```css
.box {
	display: grid | inline-grid | subgrid;
}
```

* `grid`定义了一个网格容器，它以块级元素的形式显示。
* `inline-grid`定义了一个网格容器，它以内联元素的形式显示。
* `subgrid`定义了一个网格容器，这个网格容器是其父级网格容器的一个子项。它的行和列的大小从父级网格容器中获取。

### grid-template-columns
### grid-template-rows
`grid-template-rows`和`grid-template-columns`定义了一个网格的列数、行数以及网格的大小。

```css
.box {
    grid-template-columns: <track-size> ... | <line-name> <track-size> ...;
	grid-template-rows: <track-size> ... | <line-name> <track-size> ...;
}
```

* <track-size>定义网格单元的宽高，其单位可以是一个`长度`(如`px`、`em`、`rem`、`vw`、`vh`)或`百分比`，也可以是网格中自由空间的份数(单位为`fr`)。
* <line-name>定义网格线的名称，它不是必须值。可以一个你选择的任意名字，当没有显示设定时，它的名字以数字表示。

例如：

```css
.box {
	grid-template-columns: 40px 50px auto 50px 40px;
	grid-template-rows: 25% 100px auto;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-28.png)

为了更好地语义化，我们可以给网格线指定一个名字，注意网格线命名时的中括号语法：

```css
.box {
	grid-template-columns: [first] 40px [line2] 50px [line3] auto [col4-start] 50px [five] 40px [end];
	grid-template-rows: [row1-start] 25% [row1-end] 100px [third-line] auto [last-line];
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-29.png)

一根网格线可以有多个名字，例如在下面的例子中第二根线有两个名字：row1-end 和 row2-start，命名方式以空格来作为间隔。

```css
.box {
	grid-template-rows: [row1-start] 25% [row1-end row2-start] 25% [row2-end];
}
```

众所周知：程序员是不喜欢写重复的代码的，如果我们定义了容器的重复部分，你可以使用CSS的`repeat()`方法来生成多个相同值：

```css
.box {
	grid-template-columns: repeat(3, 20px [col-start]) 5%;
}
```

上面的代码等价于

```css
.box {
	grid-template-columns: 20px [col-start] 20px [col-start] 20px [col-start] 5%;
}
```

`fr`是一个特殊的单位，它可以类似于设定`flex-grow`时，给网格容器中的自由空间设置为一个份数，举个例子，下面的例子将把网格容器的每个子项设置为三分之一：

```css
.box {
	grid-template-columns: 1fr 1fr 1fr;
}
```

也是类似于`flex-grow`，自由空间是在固定子项确定后开始计算的（这里就如同`flex-basis`提前给予宽高那样），在下面的例子中自由空间是`fr`单位的总和但不包括`50px`：

```css
.box {
	grid-template-columns: 1fr 50px 1fr 1fr;
}
```

### grid-template-areas
`grid-template-areas`可以配合`grid-area`定义一个显式的网格区域。`grid-template-areas`定义网格区域，然后使用`grid-area`调用声明好的网格区域名称来放置对应的网格项目。

如下列例子所示：[grid-template-areas demo](http://www.xingbofeng.com/css-grid-flex/demo/demo7.html)

```html
<section class="grid">
	<div class="title">title</div>
	<div class="nav">nav</div>
	<div class="main">main</div>
	<div class="aside">aside</div>
	<div class="footer">footer</div>
</section>
```

```css
.grid {
	display: grid;
	grid-template-columns: 100px 100px 100px 100px 100px;
	grid-template-rows: 100px 100px 100px 100px;
	grid-template-areas: 'title title title title aside'
				 		 'nav main main main aside'
				 		 'nav main main main aside'
				 		 'footer footer footer footer footer';
	font-size: 30px;
	text-align: center;
}
.title {
	grid-area: title;
	background-color: blue;
}
.nav {
	grid-area: nav;
	background-color: yellow;
}
.main {
	grid-area: main;
	background-color: gray;
}
.aside {
	grid-area: aside;
	background-color: green;
}
.footer {
	grid-area: footer;
	background-color: pink;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-30.jpg)

### grid-column-gap
### grid-row-gap
`grid-column-gap`和`grid-row-gap`定义了网格之间的间距。

```css
.box {
	grid-column-gap: <line-size>;
	grid-row-gap: <line-size>;
}
```

例如：

```css
.box {
	grid-template-columns: 100px 50px 100px;
	grid-template-rows: 80px auto 80px;
	grid-column-gap: 10px;
	grid-row-gap: 15px;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-31.png)

**注意**：`grid-column-gap`与`grid-row-gap`定义的值不包括网格项目到容器边缘的间距。

### justify-items
`justify-items`定义了网格子项的内容和列轴对齐方式，即水平方向上的对齐方式。

```css
.box {
	justify-items: start | end | center | stretch;
}
```

* `start`代表内容和网格区域的左边对齐。
* `end`代表内容和网格区域的右边对齐。
* `center`代表内容和网格区域的中间对齐。
* `stretch`为默认值，代表填充整个网格区域的宽度。

显而易见，类似于`flex`布局方式，利用此属性，我们能很容易地实现`水平居中`了。

举例：

```css
.box {
	justify-items: start;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-32.png)

```css
.box {
	justify-items: end;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-33.png)

```css
.box {
	justify-items: center;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-34.png)

```css
.box {
	justify-items: stretch;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-35.png)

此外，我们可以通过对`grid项目`设定`justify-self`属性把这个行为设置到单独的网格子项。

### align-items

类似于`justify-items`，`align-items`定义了网格子项的内容和行轴对齐方式，即垂直方向上的对齐方式。

```css
.box {
	align-items: start | end | center | stretch;
}
```

* `start`代表内容和网格区域的上边对齐。
* `end`代表内容和网格区域的下边对齐。
* `center`代表内容和网格区域的中间对齐。
* `stretch`为默认值，代表填充整个网格区域的高度。

显而易见，类似于`flex`布局方式，利用此属性，我们能很容易地实现`垂直居中`了。

举例：

```css
.box {
	align-items: start;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-36.png)

```css
.box {
	align-items: end;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-37.png)

```css
.box {
	align-items: center;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-38.png)

```css
.box {
	align-items: stretch;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-35.png)

此外，我们可以通过对`grid项目`设定`align-self`属性把这个行为设置到单独的网格子项。

### justify-content

实际上在使用中可能出现这种情况：网格总大小比它的网格容器的容量小，导致这个问题的原因可能是所有网格子项都使用了固定值，比如`px`。`justify-content`属性定义了网格和网格容器列轴对齐方式（和`align-content`相反，它是和行轴对齐）。

```css
.box {
	justify-content: start | end | center | stretch | space-around | space-between | space-evenly;
}
```

这个属性很类似于`Flexbox`的`justify-content`属性：

* `start`代表网格在网格容器左边对齐。
* `end`代表网格在网格容器右边对齐。
* `center`代表网格在网格容器中间对齐。
* `stretch`改变网格子项的容量让其填充整个网格容器宽度。
* `space-around`代表在每个网格子项中间放置均等的空间，在始末两端只有一半大小。
* `space-between`代表在每个网格子项中间放置均等的空间，在始末两端没有空间。
* `space-evenly`代表在每个网格子项中间放置均等的空间，包括始末两端。

举例：
```css
.box {
	justify-content: start;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-39.png)

```css
.box {
	justify-content: end;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-40.png)

```css
.box {
	justify-content: center;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-41.png)

```css
.box {
	justify-content: stretch;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-42.png)

```css
.box {
	justify-content: space-around;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-43.png)

```css
.box {
	justify-content: space-between;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-44.png)

```css
.box {
	justify-content: space-evenly;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-45.png)

### align-content

类似于`justify-content`，`align-content`属性定义了网格和网格容器行轴对齐方式。

```css
.box {
	align-content: start | end | center | stretch | space-around | space-between | space-evenly;
}
```

* `start`代表网格在网格容器上边对齐。
* `end`代表网格在网格容器下边对齐。
* `center`代表网格在网格容器中间对齐。
* `stretch`改变网格子项的容量让其填充整个网格容器高度。
* `space-around`代表在每个网格子项中间放置均等的空间，在始末两端只有一半大小。
* `space-between`代表在每个网格子项中间放置均等的空间，在始末两端没有空间。
* `space-evenly`代表在每个网格子项中间放置均等的空间，包括始末两端。

举例：
```css
.box {
	align-content: start;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-46.png)

```css
.box {
	align-content: end;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-47.png)

```css
.box {
	align-content: center;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-48.png)

```css
.box {
	align-content: stretch;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-49.png)

```css
.box {
	align-content: space-around;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-50.png)

```css
.box {
	align-content: space-between;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-51.png)

```css
.box {
	align-content: space-evenly;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-52.png)

### grid-auto-columns
### grid-auto-rows
根据前面所学可知，`grid-template-columns`、`grid-template-rows`和`grid-template-areas`三个属性可以定义一个显式的网格，确定网格的轨道以及网格行数和列数的明确数量。
`grid-auto-columns`与`grid-auto-rows`可以指定隐式网格。

```css
.box {
	grid-auto-columns: <track-size> ...;
	grid-auto-rows: <track-size> ...;
}
```

因为隐式网格的概念比较抽象，这里举例子来进行说明：

我先写了以下代码：

```html
<div class="grid">
	<div class="box1">box1</div>
	<div class="box2">box2</div>
	<div class="box3">box3</div>
	<div class="box4">box4</div>
</div>
```

```css
.grid {
	display: grid;
	grid-template-columns: 200px;
	grid-template-rows: 200px;
	text-align: center;
	font-size: 30px;
}
.box1 {
	background-color: pink;
	grid-column: 1;
	grid-row: 1;
}
.box2 {
	background-color: yellow;
	grid-column: 2;
	grid-row: 1;
}
.box3 {
	background-color: gray;
	grid-column: 1;
	grid-column: 2;
}
.box4 {
	background-color: blue;
	grid-column: 2;
	grid-row: 2;
}
```

因为我们只给了网格容器一个网格单元，即我们只创建了一个`1×1的网格`，并且没有指定`grid-auto-columns`与`grid-auto-rows`属性，在浏览器中渲染出来是这样的：

![image](http://oczira72b.bkt.clouddn.com/grid-flex-54.jpg)

现在，我们可以通过`grid-auto-columns`与`grid-auto-rows`属性，创建一个隐式的`2×2的网格`。

给上述代码的`.grid`添加如下两条属性：

```css
grid-auto-columns: 300px;
grid-auto-rows: 300px;
```

现在我们就能正常显示出这样的隐式网格了：

![image](http://oczira72b.bkt.clouddn.com/grid-flex-55.jpg)

您可以[点此](http://www.xingbofeng.com/css-grid-flex/demo/demo8.html)查看demo。

### grid-auto-flow

像刚才我们没有添加`grid-auto-columns`与`grid-auto-rows`属性时，网格也类似于自动放置到了应该放置的位置了。

其实`grid布局`自身具有的自动布局算法会将网格子项自动放置起来，而`grid-auto-flow`属性控制自动布局算法如何工作。

```css
.box {
	grid-auto-flow: row | column | row dense | column dense
}
```

* `row`为默认值，代表自动布局算法在每一行中依次填充，只有必要时才会添加新行。
* `column`代表自动布局算法在每一列中依次填充，只有必要时才会添加新行。
* `dense`代表告诉自动布局算法如果更小的子项出现时尝试在网格中填补漏洞。

我们尽量不要将这个属性设置为`dense`，因为它可能让我们的页面布局产生混乱。

举个例子：

```html
<section class="container">
    <div class="item-a">item-a</div>
    <div class="item-b">item-b</div>
    <div class="item-c">item-c</div>
    <div class="item-d">item-d</div>
    <div class="item-e">item-e</div>
</section>
```

```css
.container {
    display: grid;
    grid-template-columns: 60px 60px 60px 60px 60px;
    grid-template-rows: 30px 30px;
    grid-auto-flow: row;
}
```

在这个例子中，我们创建了一个`5×2的网格`，并设置`grid-auto-flow`为`row`。

但是当我们要网格中放置子项时，你只能为其中2个分配位置：

```css
.item-a{
    grid-column: 1;
    grid-row: 1 / 3;
}
.item-e{
    grid-column: 5;
    grid-row: 1 / 3;
}
```

此时在页面中它会这样显示：

![image](http://oczira72b.bkt.clouddn.com/grid-flex-56.png)

但如果我们把`grid-auto-flow`设定为`column`，它将呈现为这样的情况：

![image](http://oczira72b.bkt.clouddn.com/grid-flex-57.png)

### grid
`grid`为以下属性的合并写法：`grid-template-rows`，`grid-template-columns`，`grid-template-areas`，`grid-auto-rows`，`grid-auto-columns`，`grid-auto-flow`。它也可以设置`grid-column-gap`和`grid-row-gap`。

```css
.box {
    grid: none | <grid-template-rows> / <grid-template-columns> | <grid-auto-flow> [<grid-auto-rows> [/ <grid-auto-columns>]];
}
```

其中`none`代表一切值均为初始值。

举个例子，下面两段代码是等价的：

```css
.box {
	grid: 200px auto / 1fr auto 1fr;
}
```

```css
.box {
    grid-template-rows: 200px auto;
    grid-template-columns: 1fr auto 1fr;
    grid-template-areas: none;
}
```

下面两段代码也是等价的：

```css
.box {
    grid: column 1fr / auto;
}
```

```css
.box {
    grid-auto-flow: column;
    grid-auto-rows: 1fr;
    grid-auto-columns: auto;
}
```

注：就我个人而言，不建议使用合并写法，这样会让代码的维护者难以阅读。

参考资料：
* [complete-guide-grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
* [css3-grid-layout](https://www.w3.org/TR/css3-grid-layout/)
* [grid-layout](https://github.com/airen/grid-layout)
* [Grid 的完整介绍（二）](http://zhaozhiming.github.io/blog/2017/01/09/complete-guide-grid-zhcn-part2/)