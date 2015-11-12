---
layout: default
title: css基础复习
---

##{{ page.title }}

>####作者:admos_han 

>####日期:{{ page.date | date_to_string }}

>上次发现，在IE8下，a元素内如果为空，则此a元素不起作用

>css中百分比的计算：是根据其父元素的宽度来计算的，比如，我们使用百分比来设置一个元素的宽，那么这个宽的计算是由其父元素的宽度和百分比来计算得到的，同样，对于一般元素设置其高为百分比，是相对父元素的高。稍微违背常识的是，设置padding，或者margin的高度是由父元素的宽度和这个百分比设置得到的 ,对于margin，还有一个需要注意的地方，就是子元素的margin会同样作用于父元素上

```html

<!DOCTYPE html>
<html>
<head>
	<title>canvas_css by admos</title>
	<meta charset='utf-8'>
	<style type="text/css">
	html,body{
	margin:0px;
	height:100%;
	}
	.child{
		margin: 50%;
	}
	.canvas{
		width: 50%;
		height: 50%;
		background-color: red;
		
	}
	</style>
</head>
<body>
<div class="canvas">
	<div class="child">sdsad</div>
</div>
	<!-- <canvas>你的浏览器不支持canvas</canvas> -->
</body>
<script type="text/javascript" src="index.js"></script>
</html>

```

>margin折叠的问题，老问题，当我没有给父元素设置**overflow:hidden** 或者 border 为**none**的时候，子元素设置margin反而会作用到父元素身上。

>关于margin元素的奇怪表现：相关解释是：

这个“问题”……它是CSS2.1的盒模型中规定的内容——Collapsing margins：

In this specification, the expression collapsing margins means that adjoining margins (no non-empty content, padding or border areas or clearance separate them) of two or more boxes (which may be next to one another or nested) combine to form a single margin. 所有毗邻的两个或更多盒元素的margin将会合并为一个margin共享之。毗邻的定义为：同级或者嵌套的盒元素，并且它们之间没有非空内容、Padding或Border分隔。
　　这就是原因了。“嵌套”的盒元素也算“毗邻”，也会 Collapsing Margins。这个合并Margin其实很常见，就是文章段落元素<p/>，并列很多个的时候，每一个都有上下1em的margin，但相邻的<p/>之间只会显示1em的间隔而不是相加的2em。这个很好理解，我就是奇怪为什么W3C要让嵌套的元素也共享Margin，想不出来在什么情况下需要这样的表现。 　　这个问题的避免方法很多，只要破坏它出现的条件就行。给 Outer Div 加上 padding/border，或者给 Outer Div / Inner Div 设置为 float/position:absolute(CSS2.1规定浮动元素和绝对定位元素不参与Margin折叠)。 　　更多信息，关于不同值的margin折叠后表现的计算方法等等，可自行查阅W3C的CSS2.1规范

>对于定位为absolute的，当left或top取一个很大的正值，会出现滚动条，relative则会隐藏。想想肯定是正值，因为负值会出现这样一种滚动条，向上滚的滚动条，或者向左的滚动条。当取极大的负值的时候会直接隐藏。这个可能会有点用。

