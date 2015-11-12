---
layout: default
title: 写控件中遇到的小问题
---

##{{ page.title }}

>####作者:admos_han 

>####日期:{{ page.date | date_to_string }}

>先说关于博客上的一个小问题，我个人是偏爱markdown的，简单有效，但是发现git page上markdown确实有挺大问题的，打算弃用了，还是用html来写好了，写几个控件装饰一下。

>给一个div块设置min-width时，发现min-width不起作用，这里其实有个理解上的问题，不是min-width不起作用了，而是min-width  要在宽度小于一定宽度的情况下才能看得出来，你外面的宽度够宽是看不出来效果的。而min-height则不一样，min-height一下子就能看出效果（在你默认高度的情况下），因为高度的默认值是0px；这两者的不同表现不是由于本身，而是浏览器对于宽高的默认值不同，对于宽的默认是撑满，对于高的默认是0.除非里面有子元素来撑高它。

>调试过程中发现，在h5里面，要特别小心display设置为inline-block，里面有文字，那么文字的font-size会影响高度，特别是你设置了height为百分数的时候。

>使得块级元素水平垂直居中，一个比较好用的方法是利用绝对定位，使得position为absolute，然后设置它的四个方向为0px;再设置margin为auto;原理是这样的一个元素不可能距离上面是0和下面是0，所以它只能垂直居中了。
其他还有一些方法，无非利用 margin auto,浮动，lineheight，display为table或者inline-block。水平居中的方法很多，垂直居中要费事点，我会陆续来总结。