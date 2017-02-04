# flex基础语法介绍

《轴线与网格》里主要讲述了`grid`与`flex`中，网格与轴线的基本概念，了解了这些基本概念之后，我们可以更轻松地对布局方式进行研究，这一篇文章主要描述`flex`布局中，定义在容器与项目的相关属性。

本篇文章是依据我个人的所学所知，且部分参考国内外优秀的`flex布局`的相关文献总结而得。

## 定义在容器的属性
### disaplay
`display`属性定义了一个弹性盒子容器，容器是展现为行内或块状由所给定的值而决定，此时，他的所有子元素进入flex文档流，称为伸缩项目。
```css
.box {
    display: flex;
}
```
定义行内容器的flex布局：
```css
.box {
    display:inline-flex;
}
```
对于safiri浏览器，需要加上`webkit`前缀（以前遇到过，深坑啊！）
```css
.box {
    display:webkit-flex;
    display:flex;
}
```
此外，请注意以下两点：
* CSS的columns在伸缩容器上没有效果。
* float、clear和vertical-align在伸缩项目上没有效果。
### flex-direction
`flex-direction`定义主轴的方向。因主轴是二维空间的矢量，因此`flex-direction`有四个值，分别代表了x轴与y轴的正方向与反方向。
```css
.box {
    flex-direction: row | row-reverse | column | column-reverse;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-5.jpg)


* `row`为默认值，代表主轴为水平轴，方向为从左到右。
* `row-reverse`代表主轴为水平轴，方向为从右到左。
* `column`代表主轴为垂直轴，方向为从上到下。
* `column-reverse`代表主轴为垂直轴，方向为从下到上。

### flex-wrap
`flex-wrap`定义`flex项目`是否换行显示。默认情况下，`flex项目`会尽可能地显示在一行当中，即默认值为`nowarp`。
```css
.box {
    flex-wrap: nowrap | wrap | wrap-reverse;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-6.jpg)

* `nowrap`为默认值，代表不换行。
* `wrap`代表换行，但默认为第一行在上方。
* `wrap-reverse`代表换行，但默认为第一行在下方。

### flex-flow
`flex-flow`是`flex-direction`和`flex-wrap`的合并写法，它同时定义了`主轴方向`与容器内项目的`换行方式`，其默认值为`row nowarp`
```css
.box {
    flex-flow: <‘flex-direction’> || <‘flex-wrap’>;
}
```

### justify-content
`justify-content`定义了项目在主轴上的对齐方式，但请注意：`justify-content`只会在主轴项目仍具有剩余空间时才会起作用。

利用此API，我们便能很容易地实现：`等分宽高`了。
```css
.box {
    justify-content: flex-start | flex-end | center | space-between | space-around;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-7.jpg)

* `flex-start`为默认值，代表项目在主轴上向起始方向对齐。
* `flex-end`代表项目在主轴上向结束方向对齐。
* `center`代表项目在主轴上居中对齐。
* `space-between`代表项目在主轴上两端对齐，但第一个项目在主轴的起始位置，最后一个项目在主轴的结束位置。
* `space-around`代表项目在主轴上等分间距，但第一个项目与最后一个项目距离主轴的两端保持一定的距离，这个距离为项目之间间距的1/2。

### align-items
`align-items`定义了项目在交叉轴上的对齐方式。可以把它想像成交叉轴的`justify-content`。

```css
.box {
    align-items: flex-start | flex-end | center | baseline | stretch;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-8.jpg)

* `flex-start`代表项目在交叉轴上向起始方向对齐。
* `flex-end`代表项目在交叉轴上向结束方向对齐。
* `center`代表项目在交叉轴上居中对齐。
* `baseline`代表项目在交叉轴上向项目的第一行文字的基线对齐。
* `stretch`代表项目在交叉轴上拉伸对齐。

### align-content
当我们把容器的`flex-warp`的值设置为`warp`或者`warp-reverse`时，若项目不能在一根主轴上显示，容器便会出现多根主轴。

此时便需要一个值来定义多根平行轴线的对齐方式，这个值便是`align-content`。

```css
.box {
    align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-9.jpg)

* `flex-start`代表多条平行的主轴在交叉轴的起始位置对齐。
* `flex-end`代表多条平行的主轴在交叉轴的结束位置对齐。
* `center`代表多条平行的主轴在交叉轴上居中对齐。
* `space-between`代表多条平行的主轴在交叉轴上两端对齐，但第一条主轴在交叉轴的起始位置，最后一条主轴在交叉轴的结束位置。
* `space-around`代表多条平行的主轴在交叉轴上等分间距，但第一条主轴与最后一条主轴距离主轴的两端保持一定的距离，这个距离为其它主轴之间间距的1/2。
* `stretch`为默认值，代表多条平行的主轴拉伸对齐。

## 定义在项目上的属性
### order
`order`定义项目在主轴上的排列顺序。数值越小，排列越靠前，默认值为0。

在默认情况下，项目在主轴上的排列顺序是依据它们在`HTML文档`中出现的先后顺序排列的。因我们可以通过控制文档流的先后顺序，故此API的使用情况不太普遍。

```css
.item {
    order: <integer>;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-10.jpg)

### flex-grow
`flex-grow`定义了项目的放大比例。如果所有伸缩项目的`flex-grow`设置了`1`，那么每个伸缩项目将设置为一个大小相等的剩余空间。如果你给其中一个伸缩项目设置了`flex-grow`值为`2`，那么这个伸缩项目所占的剩余空间是其他伸缩项目所占剩余空间的`两倍`。

注意：负值对该属性无效。

```css
.item {
    flex-grow: <number>; /* default 0 */
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-11.jpg)

### flex-shrink
类似于`flex-grow`，`flex-shrink`定义了项目的缩小比例。其默认值为`1`。

如果所有项目的`flex-shrink`都为`1`，当空间不足时，都将等比例缩小。

如果所有项目都为`1`，但其中一个项目的`flex-shrink`为`0`，即代表空间不足时，该项目缩小0倍，即为不缩小。

注意：负值对该属性不起作用。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-12.jpg)

### flex-basis
`flex-basis`定义了在分配多余空间之前，项目占据的主轴空间。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为`auto`，即项目的本来大小。
```css
.item {
    flex-basis: <length> | auto; /* default auto */
}
```
利用`flex-basis`，我们可以很容易实现页面布局中的常见问题：[两栏/三栏布局](http://www.xingbofeng.com/css-grid-flex/demo/demo1.html)。
```html
<div class="box">
	<div class="left">left</div>
	<div class="main">main</div>
</div>
```

```css
.box {
	display: flex;
	height: 200px;
}
.left {
	background-color: yellow;
	flex-basis: 200px;
	/* flex-basis定义该项目在分配主轴空间之前提前获得200px的空间 */
	flex-grow: 0;
	/* flex-grow定义该项目不分配剩余空间 */
}
.main {
	background-color: green;
	flex-grow: 1;
	/* flex-grow定义main占满剩余空间 */
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-13.jpg)

### flex
`flex`是`flex-grow`、`flex-shrink`和`flex-basis`的简写，默认值为`0 1 auto`。后两个属性可选。
```css
.item {
    flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```

### align-self
`align-self`定义了单个项目上在交叉轴的对齐方式。
其默认值为继承容器的`align-items`属性。

具体的属性值参阅`align-items`的属性值。
```css
.item {
    align-self: auto | flex-start | flex-end | center | baseline | stretch;
}

```
![image](http://oczira72b.bkt.clouddn.com/grid-flex-14.jpg)

参考资料：

* [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* [flexbox-CSS3弹性盒模型flexbox完整版教程](http://caibaojian.com/flexbox-guide.html)
* [w3cplus：一个完整的Flexbox指南](http://www.w3cplus.com/css3/a-guide-to-flexbox.html)
* [Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
