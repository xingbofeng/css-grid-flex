# 拥抱未来的CSS布局方式：flex与grid布局

本系列文章为对`CSS`中`flex`布局与`grid`布局的详细介绍，已在[GitHub](https://github.com/xingbofeng/css-grid-flex)同步更新，如您在阅读过程中发现描述有误或错别字的情况，您可以向[本项目](https://github.com/xingbofeng/css-grid-flex)提出`issus`或`Pull Request`。

本系列文章为我在深入研究CSS的布局方式的过程中的一些总结。主要是对于CSS3标准里的`flex`布局方式CSS4草案中的`grid`布局方式进行一些总结。

## 下载本系列文章
```
git clone https://github.com/xingbofeng/css-grid-flex.git
```

## 为什么想写这系列的博文？
现今的前端开发中，页面布局主要以基于盒模型的布局方式，也就是常说的`div`+`css`。
我们通过`display`、`float`、`position`布局页面。

传统页面布局过于繁琐，代码冗余，一些功能不易于简单实现：例如垂直居中、等分宽高等。

关于更多`flex`与`grid`的思考，可以前往[前端未来页面布局发展方向是Flexbox 还是Grid？ - 前端开发- 知乎](https://www.zhihu.com/question/28691822)进行探讨。

## 为什么是“拥抱未来”？
`flex`布局又称`弹性盒子`布局，它于2009年提出，并已经进入CSS3标准。现今虽已得到众高端浏览器厂商的支持，但由于IE10以下的用户基数仍然很大，大部分Web开发者并不能够真正在某种程度上大胆尝试这种新型布局理念。

而`grid`布局则更加新奇了，甚至说到今天，连chrome这样的现代化浏览器都没有支持它。

## 准备工作

那为什么要谈它呢？

`grid`布局是2010年由`Microsoft`提出的，**目前已经成为W3C候选标准**。虽然说我们依旧不能够通过正常方式使用这样的布局方式，但我们还是通过浏览器的设置可以看到相关的效果。比如Chrome浏览器中通过`chrome://flags`打开Chrome浏览器实验网络平台功能。，将`experimental web platform features`选项设置为`enable`，这个方法同样适用于 Opera，对于Oprea来说，地址为`opera://flags`。

![image](http://oczira72b.bkt.clouddn.com/grid-flex-1.jpg)

打开后，我们将能够在浏览器中正常使用`grid`的布局方式了。

若要在项目当中使用`grid`布局方式，则可能需要安装[css-grid-polyfill](https://github.com/FremyCompany/css-grid-polyfill)。

## 鸣谢
感谢以下朋友对本仓库错误的纠正与贡献
* [spademan](https://github.com/spademan)
* [klren0312](https://github.com/klren0312)

## LICENSE
本项目采用宽泛的[MIT LICENSE](https://github.com/xingbofeng/css-grid-flex/blob/master/LICENSE)，您可以随意转载本项目，只需要保持署名即可。