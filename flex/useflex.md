# flex的相关应用

学习了`flex`相关语法之后，可能需要一些例子来说明其常见的应用场景。在这篇文章当中，我将举几个简单的例子加以说明。

## [水平/垂直居中](http://www.xingbofeng.com/css-grid-flex/demo/demo2.html)

在`flex`出来以前，我们使用各种奇淫技巧来让一个元素居中，例如`绝对定位`、`transform`、`vertical-align`等。他们都有一个普遍的特点，那就是**过于复杂**。

有了`flex`之后，我们可以通过设置`justify-content`与`align-items`的值为`center`，让项目在主轴和交叉轴居中对齐，实现[水平/垂直居中](http://www.xingbofeng.com/css-grid-flex/demo/demo2.html)

![image](http://oczira72b.bkt.clouddn.com/grid-flex-16.jpg)

```html
<div class="box">
	<div class="content">我是子元素，我要垂直居中</div>
</div>
```

```css
.box {
	display: flex;
	align-items: center;
	justify-content: center;
	height: 500px;
	width: 500px;
	background-color: green;
}
.content {
	height: 200px;
	width: 200px;
	background-color: yellow;
	line-height: 200px;
	text-align: center;
}
```


## [两栏/三栏布局](http://www.xingbofeng.com/css-grid-flex/demo/demo1.html)

在`flex`出来以前，我们使用各种奇淫技巧实现两栏/三栏布局，通过基于`float`、`margin`等来实现两栏/三栏布局，代码过于冗余。

但是现在我们可以利用`flex`，我们可以很容易实现页面布局中的常见问题：[两栏/三栏布局](http://www.xingbofeng.com/css-grid-flex/demo/demo1.html)。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-13.jpg)

```html
<div class="box">
	<div class="left">left</div>
	<div class="main">main</div>
</div>
<div class="box">
	<div class="left">left</div>
	<div class="main">main</div>
	<div class="right">right</div>
</div>
```

```css
.box {
	display: flex;
	height: 200px;
	margin-bottom: 30px;
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
.right {
	background-color: blue;
	flex-basis: 100px;
	flex-grow: 0;
}
```

## [等分宽高](http://www.xingbofeng.com/css-grid-flex/demo/demo3.html)

在常见页面布局中，我们常常遇到这样的情况：导航栏中我们需要等分宽，通常情况我们会做一个算术，计算出导航栏每项的宽度百分比。

但实际上，一旦想要增加或删除一项，我们就得重新计算，极为不方便（当然像现代化的前端框架如`React`可以带入算式计算，这里不做累述）。

有了`flex`布局方式后，做出的[等分宽高](http://www.xingbofeng.com/css-grid-flex/demo/demo3.html)就更为方便了。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-17.jpg)

```html
<nav>
	<a href="#">苟</a>
	<a href="#">利</a>
	<a href="#">国</a>
	<a href="#">家</a>
	<a href="#">生</a>
	<a href="#">死</a>
	<a href="#">以</a>
</nav>
```

```css
nav {
	display: flex;
}
a {
	flex-grow: 1;
	font-size: 30px;
	text-decoration: none;
	text-align: center;
}
```
## [圣杯布局](http://www.xingbofeng.com/css-grid-flex/demo/demo4.html)

圣杯布局也就是像下面这幅图那样：
![image](http://oczira72b.bkt.clouddn.com/grid-flex-18.png)

记得很久之前看到过的一篇文章[那些年，奇妙的圣杯与双飞翼，还有负边距](https://segmentfault.com/a/1190000004579886)，里面详细讲述了通过传统页面布局方式实现圣杯布局的过程。内容之丰富，代码之华丽。

现在有了`flex`布局之后，我们实现[圣杯布局](http://www.xingbofeng.com/css-grid-flex/demo/demo4.html)也就简单而方便。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-19.jpg)

```html
<div class="box">
	<header>header</header>
	<div class="content">
		<main>main</main>
		<nav>nav</nav>
		<aside>aside</aside>
	</div>
	<footer>footer</footer>
</div>
```

```css
.box {
	display: flex;
	flex-direction: column;
	width: 100%;
	height: 500px;
	background-color: yellow;
	text-align: center;
	font-size: 30px;
}
header, footer {
	flex: 0 0 80px;
	line-height: 80px;
}
header {
	background-color: pink;
}
footer {
	background-color: gray;
}
.content {
	display: flex;
	flex: 1;
}
nav {
	order: -1;
	background-color: blue;
	flex: 0 0 80px;
}
aside {
	background-color: green;
	flex: 0 0 80px;
}
main {
	flex: 1;
}
```

## [固定底栏](http://www.xingbofeng.com/css-grid-flex/demo/demo4.html)

在刚才的`圣杯布局`中，如果整个容器的内容并不是那么多，`footer`便会提升到上边，显得十分不好看。

我们给圣杯布局的`容器 .box`加上`min-height:100vh;`，让它的最小高度占满整个浏览器窗口。由于我们的`content`的`flex-grow`属性为`1`，我们便能够让主体部分的高度占满剩余高度了，而不是要去使用`CSS3`的`calc()`这个API进行高度计算了。

## [流式布局](http://www.xingbofeng.com/css-grid-flex/demo/demo5.html)

在实际运用中我们通常会遇到：容器中，每行的项目数固定，并自动分行的情况。

如图所示：

![image](http://oczira72b.bkt.clouddn.com/grid-flex-20.jpg)

![image](http://oczira72b.bkt.clouddn.com/grid-flex-21.jpg)

![image](http://oczira72b.bkt.clouddn.com/grid-flex-24.jpg)

```html
<h1>10个</h1>
<div class="box">
	<div class="content"></div>
	<div class="content"></div>
	<div class="content"></div>
	<div class="content"></div>
	<div class="content"></div>
	<div class="content"></div>
	<div class="content"></div>
	<div class="content"></div>
	<div class="content"></div>
	<div class="content"></div>
</div>
```

```css
.box {
	display: flex;
	flex-flow: row wrap;
	height: 300px;
	width: 400px;
	background-color: yellow;
}
.content {
	flex: 0 0 25%;
	background-color: blue;
	border: 2px solid red;
	box-sizing: border-box;
}
```

## [结合响应式布局的综合运用](http://www.xingbofeng.com/css-grid-flex/demo/demo6.html)

这是一道来自[百度前端技术学院-task10：Flexbox 布局练习](http://ife.baidu.com/2016/task/detail?taskId=10)的习题，实现以下布局方式：

![image](http://oczira72b.bkt.clouddn.com/grid-flex-23.png)

```html
<div class="box">
	<div class="box1"></div>
	<div class="box2"></div>
	<div class="box3"></div>
	<div class="box4"></div>
</div>
```

```css
.box div{
	width: 150px;
	padding: 20px;
}
.box1 {
	height: 120px;
	background-color: red;
}
.box2 {
	height: 100px;
	background-color: blue;
}
.box3 {
	height: 40px;
	background-color: pink;
}
.box4 {
	height: 200px;
	background-color: yellow;
}
@media (min-width: 640px) {
	.box {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
}
@media (max-width: 640px) {
	.box {
		display: flex;
		flex-direction: row;
		align-items: flex-start;
		justify-content: space-between;
		flex-wrap: wrap;
	}
	.box4 {
		order: -1;
	}
}
```

参考资料：
* [Flex 布局教程：实例篇](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)
* [Flexbox该怎么用以及应用场景](http://azq.space/blog/flex/)
* [百度前端技术学院-task10：Flexbox 布局练习](http://ife.baidu.com/2016/task/detail?taskId=10)
* [那些年，奇妙的圣杯与双飞翼，还有负边距](https://segmentfault.com/a/1190000004579886)
