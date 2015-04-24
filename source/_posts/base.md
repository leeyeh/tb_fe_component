title: "基础设置"
date: 2015-04-21 16:28:07
order: 1 
tags:
---
##entry.css##

*   在body上设置了**字体大小**12px, **字体**采用非衬线字体，**字体色值**为#333，**行高**22px
*   设置了基本颜色 @link-color ，并且当链接处于 :hover 状态时才添加下划线
*   `<ins>`hover状态不添加下划线

##Normalize.css/reset.css##

统一浏览器一致性，其中 Normalize.css，这是由 Nicolas Gallagher 和 Jonathan Neal 维护的一个CSS 重置样式库。
reset.css是符合贴吧业务具体需求的重置样式

##utility##
###文本色值块###
通过颜色来展示意图，这些类可以应用于链接，并且在鼠标经过时颜色可以还可以加深，就像默认的链接一样。
vip_red是超级用户经常会使用的类, 已经设置!important，不会被覆盖，请放心使用, 并且三态已经做处理
方法：通过添加类的方式来实现，注意: 为了避免被覆盖，使用！important优先级

```
   <p class="red_text">I am a demo ! </p>
   <p class="orange_text">I am a demo ! </p>
   <a class="vip_red" href="#">I am a demo ! </a>
```

###float###

将元素向左或者向右浮动, 使用了!important，避免被覆盖

*   通过添加`.pull_left`或者`.pull_right`类
```
<span class="pull_left">float left...</span> 
<span class="pull_right">float right...</span> 
```
*   方法二：使用mixins方式
```
    .element{
        .pull-left(); //or .pull-right();
    }
```
###清除浮动###
<p>通过为<code>父元素</code>添加 .clearfix 类可以很容易地清除浮动（float）。此类还可以作为 mixin 使用。</p>
*   通过添加`.clearfix`类
```
    <div class="clearfix"></div>
```
*   通过调用`.clearfix` mixins
```
    .element{
        .clearfix(); //or .pull-right();
    }
```
###图片替换###
使用`.hide_text`类或对应的mixin可以用来将元素的文本内容替换为一张背景图。</p>
*   方法一：通过添加`.hide_text`类
```
    <span class="hide_text"></span>
```
*   方法二：通过调用`.hide_text` mixins
```
   .element{
       .hide-text();
   }
```

###文字省略###
*   方法一：通过添加`.text_overflow`, text_overflow文字省略设置在dispaly： block或者dispaly
> 注意：.text_overflow类只是支持一行省略
```
<div class="text_overflow"></div>
```
*   方法二：使用mixins .text-overflow(...)
```
    .element{
        .text-overflow(); 
    }
    .element{
        .text-overflow(2); // 传入参数，仅支持webkit，表示第几行省略
    }
```
##button##
跨浏览器展现

据bootstrap的介绍，**强烈建议尽可能使用 `<button>`元素**来获得在各个浏览器上获得相匹配的绘制效果。

同时，如果并排按钮，建议使用同类型的标签，禁止lineheight的设置，因为在不同类型的按钮中，高度获取不一致

##可以作为按钮使用的标签和元素##

为 `<a>`、`<button>`、`<input type="submit">`、`<input type="button">`或 `<input type="reset">`元素添加按钮类（button class）即可使用 基础库 提供的样式。</p>

##预定义样式##
在预定义样式中，
提供了**四种样式**类: *.btn_default*、*.btn_default*、*.btn_default*、*.btn_default*
提供了**三种尺寸**类: *.btn_small*、*.btn_middle*、*.btn_larger*
这四种样式和尺寸可以随意搭配使用。

###demo--样式###
<button class="btn_default btn_small" >常用蓝色(.btn_default)</button>
<button class="btn_attention btn_small" >关注(.btn_attention)</button>
<button class="btn_sub btn_small" >副按钮(.btn_sub)</button>
<button class="btn_disable btn_small" >不可用按钮(.btn_disable)</button>

```
<button class="btn_default btn_small" >常用蓝色(.btn_default)</button>
<button class="btn_attention btn_small" >关注(.btn_attention)</button>
<button class="btn_sub btn_small" >副按钮(.btn_sub)</button>
<button class="btn_disable btn_small" >不可用按钮(.btn_disable)</button>
```

###demo--尺寸###
<button class="btn_default btn_small" >常用尺寸(.btn_small)</button> 
<button class="btn_default btn_middle" >中按钮(.btn_middle)</button> 
<button class="btn_default btn_larger" >大按钮(.btn_larger)</button> 
```
<button class="btn_default btn_small" >常用尺寸(.btn_small)</button> 
<button class="btn_default btn_middle" >中按钮(.btn_middle)</button> 
<button class="btn_default btn_larger" >大按钮(.btn_larger)</button> 
```

##自定义按钮##
自定义按钮提供了以下两种mixins

```
//纯色背景
.btn-variant(@color, @bg-color, @border-color, @hover-color, @hover-bg-color, @hover-border-color){
}

//渐变背景
.btn-styles(@color: #fff, @btn-color: #555) {
}

//@padding-vertical: btn上下间距 
//@padding-horizontal: btn横向间距 
//@line-height: btn字体大小
//@font-size: btn字体大小
//@border-radius: btn圆角
.btn-size(@padding-vertical, @padding-horizontal, @line-height, @font-size, @border-radius) {
}

```

自定义按钮是以btn为基础，
*   如果和预定义样式中的4类样式不一致，建议使用.btn-variant(...)或者.btn-styles(...)进行设置;
> 如果使用自定义样式，请不要再添加.btn_default, .btn_sub等预定义样式
*   如果和预定义样式中的3类尺寸不一致，建议使用.btn-size(...)进行设置;
> 如果使用自定义尺寸，请不要再添加.btn_small, .btn_middle等预定义尺寸

```
<input type="button" value="test"/ class="btn my_btn">

.my_btn{
   .btn-styles(#fff, #555);
}

```

##带icon的按钮##

使用<code>&lt;i&gt;</code>表示icon, 样式由用户自己定义，可以使用sprite图片，同时可以使用iconfont</p>

*   如果使用sprite图片, 使用了icon::before绝对定位的方式，原因是: 为了浏览器兼容性，使用padding值实现了btn的垂直尺寸，如果icon图片尺寸超出12px，会出现btn被撑高</p>
*   如果使用sprite图片, icon::before, Ie8及之下不支持，如果需要兼容到ie8，请在外层容器btn_with_icon设置relative属性</p>

暂时还确实iconfont，之后会补充</p>

```
<button class="btn_sub btn_small btn_with_icon"><i class="icon_attention"></i>关注</button>
<button class="btn_attention btn_small btn_with_icon"><i class="icon_attention"></i>关注</button>

.btn_with_icon{
    padding-left: 24px;
    .icon_attention{
        position: relative;
        &::before{
            position: absolute;
        }
    }
} 

```