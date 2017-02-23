# grid的相关应用

学习了`grid`相关语法之后，可能需要一些例子来说明其常见的应用场景。在这篇文章当中，我将举几个简单的例子加以说明。

类似于`flex`那几个例子，也是较为常见的使用场景。

## [水平/垂直居中](http://www.xingbofeng.com/css-grid-flex/demo/demo9.html)

类似于`flex`，我们，我们可以通过设置`justify-items`与`align-items`的值为`center`，让仅有一个网格单元的容器内的网格项目在网格容器中水平垂直居中对齐，实现[水平/垂直居中](http://www.xingbofeng.com/css-grid-flex/demo/demo2.html)

![image](http://oczira72b.bkt.clouddn.com/grid-flex-16.jpg)

```html
<div class="box">
	<div class="content">我是子元素，我要垂直居中</div>
</div>
```

```css
.box {
	display: grid;
	align-items: center;
	justify-items: center;
	height: 500px;
	width: 500px;
	background-color: green;
}
.content {
	width: 200px;
	height: 200px;
	background-color: yellow;
	line-height: 200px;
	text-align: center;
}
```

## [两栏/三栏布局](http://www.xingbofeng.com/css-grid-flex/demo/demo10.html)

现在我们不仅可以利用`flex`，也可以使用`grid`，轻松实现页面布局中的常见问题：[两栏/三栏布局](http://www.xingbofeng.com/css-grid-flex/demo/demo10.html)。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-13.jpg)

```html
<div class="box box1">
	<div class="left">left</div>
	<div class="main">main</div>
</div>
<div class="box box2">
	<div class="left">left</div>
	<div class="main">main</div>
	<div class="right">right</div>
</div>
```

```css
.box {
	display: grid;
	height: 200px;
	width: 100%;
	margin-bottom: 30px;
	grid-template-columns: 200px auto;
}
.box1 {
	grid-template-columns: 200px auto;
}
.box2 {
	grid-template-columns: 200px auto 100px;
}
.left {
	background-color: yellow;
	grid-area: 1/ 1/ 2/ 2;
}
.main {
	background-color: green;
	grid-area: 1/ 2/ 2/ 3;
}
.right {
	background-color: blue;
	grid-area: 1/ 3/ 2/ 4;
}
```

## 等分宽高
等分宽高这种情况，认真看完`grid`的相关语法后都不用思考就能做的，这里就不做具体阐述了。

## [圣杯布局](http://www.xingbofeng.com/css-grid-flex/demo/demo11.html)

使用`grid`也是十分容易就能实现[圣杯布局](http://www.xingbofeng.com/css-grid-flex/demo/demo11.html)了，而且具有良好的语义化。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-70.jpg)

```html
<div class="box">
		<header>header</header>
		<main>main</main>
		<nav>nav</nav>
		<aside>aside</aside>
		<footer>footer</footer>
</div>
```

```css
* {
	margin:0;
	padding: 0;
}

.box{
	display: grid;
	width: 100vw;
	height: 100vh;
	grid-template-columns:80px 1fr 1fr 1fr 80px;
	grid-template-rows:80px 1fr 1fr 80px;
	grid-template-areas:'title title title title title '
						'nav main main main aside'
						'nav main main main aside'
						'footer footer footer footer footer';
	font-size: 30px;
	text-align: center;
}

header{
	grid-area:title;
	background-color: blue;
}
nav{
	grid-area:nav;
	background-color: red;
}

main{
	grid-area:main;
	background-color: gray;
}

aside{
	grid-area:aside;
	background-color: yellow;
}

footer{
	grid-area:footer;
	background-color: green;
}
```

这里就简单举了几个较为常见的例子加以说明。俗话说：纸上得来终觉浅，绝知此事要躬行。所有代码都是我个人亲手码的，在真正实践探索中慢慢也就能掌握了。

~~(全剧终)~~