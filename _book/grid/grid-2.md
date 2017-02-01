# grid基础语法介绍(下)

前一篇文章详细阐述了定义在`grid`容器上的各项属性，在这一篇文章里，主要是阐述`grid`布局中定义在网格项目的各项属性。

### grid-column-start
### grid-column-end
### grid-row-start
### grid-row-end
* `grid-column-start`定义了网格项目垂直方向的开始位置网格线。
* `grid-column-end`定义了网格项目垂直方向的结束位置网格线。
* `grid-row-start`定义了网格项目水平方向的开始位置网格线。
* `grid-row-end`定义了网格项目水平方向的结束位置网格线。

```css
.item {
	grid-column-start: <number> | <name> | span <number> | span <name> | auto
	grid-column-end: <number> | <name> | span <number> | span <name> | auto
	grid-row-start: <number> | <name> | span <number> | span <name> | auto
	grid-row-end: <number> | <name> | span <number> | span <name> | auto
}
```

它们的值默认为`auto`，也可以是网格线的名字，也可以是`span`加上一条网格线的名称。

* `<line>`表示网格线名称。
* `span <number>`表示子项将跨越指定数字数目的网格轨迹。
* `span <name>`表示子项将跨越到指定名字之前的网格线。
* `auto`表示自动布局，自动跨越或者默认跨越一个。

举个例子：

```css
.item-a {
	grid-column-start: 2;
	grid-column-end: five;
	grid-row-start: row1-start;
	grid-row-end: 3;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-58.png)

我们也可以使用`span`关键字

```css
.item-b {
	grid-column-start: 1;
	grid-column-end: span col4-start;
	grid-row-start: 2
	grid-row-end: span 2
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-59.png)

注：如果没有显式设置`grid-column-end/grid-row-end`，网格子项将默认跨越一个网格单元。此外，网格子项可以互相重叠，你可以使用`z-index`来控制他们的层叠顺序。

### grid-column
### grid-row
`grid-column`与`grid-row`表示`grid-column-start + grid-column-end`，和`grid-row-start + grid-row-end`的简写形式。

```css
.item {
	grid-column: <start-line> / <end-line> | <start-line> / span <value>;
	grid-row: <start-line> / <end-line> | <start-line> / span <value>;
}
```

它的值设置为`<start-line> / <end-line>`，它们同样可以传入`span`。

```css
.item-c {
	grid-column: 3 / span 2;
	grid-row: third-line / 4;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-60.png)

### grid-area

`grid-area`调用`grid-template-areas`属性创建的模板。同时，这个属性也可以是`grid-row-start+ grid-column-start + grid-row-end+ grid-column-end`的缩写。

```css
.item {
	grid-area: <name> | <row-start> / <column-start> / <row-end> / <column-end>;
}
```

注意它的参数的顺序为：`<row-start> / <column-start> / <row-end> / <column-end>`。

在上一篇文章的`grid-template-areas`中已经详细讲述通过调用`grid-template-areas`属性创建的模板的用法，详情可见
[grid-template-areas demo](http://www.xingbofeng.com/css-grid-flex/demo/demo7.html)

它也可以作为`grid-row-start+ grid-column-start + grid-row-end+ grid-column-end`的缩写形式。

```css
.item-d {
	grid-area: 1 / col4-start / last-line / 6
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-61.png)

### justify-self

`justify-self`定义了该网格单元的内容和列轴对齐方式，即水平方向上的对齐方式。

```css
.box {
	justify-self: start | end | center | stretch;
}
```

* `start`代表该网格单元和网格区域的左边对齐。
* `end`代表该网格单元和网格区域的右边对齐。
* `center`代表该网格单元和网格区域的中间对齐。
* `stretch`为默认值，代表填充整个网格区域的宽度。

```css
.item-a {
	justify-self: start;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-62.png)

```css
.item-a {
	justify-self: end;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-63.png)

```css
.item-a {
	justify-self: center;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-64.png)

```css
.item-a {
	justify-self: stretch;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-65.png)

### align-self

类似于`justify-self`，`align-self`定义了该网格单元的内容和水平轴对齐方式，即垂直方向上的对齐方式。

```css
.box {
	align-self: start | end | center | stretch;
}
```

* `start`代表该网格单元和网格区域的上边对齐。
* `end`代表该网格单元和网格区域的下边对齐。
* `center`代表该网格单元和网格区域的中间对齐。
* `stretch`为默认值，代表填充整个网格区域的高度。

```css
.item-a {
	align-self: start;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-66.png)

```css
.item-a {
	align-self: end;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-67.png)

```css
.item-a {
	align-self: center;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-68.png)

```css
.item-a {
	align-self: stretch;
}
```

![image](http://oczira72b.bkt.clouddn.com/grid-flex-69.png)

参考资料：
* [complete-guide-grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
* [css3-grid-layout](https://www.w3.org/TR/css3-grid-layout/)
* [grid-layout](https://github.com/airen/grid-layout)
* [Grid 的完整介绍（三）](http://zhaozhiming.github.io/blog/2017/01/10/complete-guide-grid-zhcn-part3/)