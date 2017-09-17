# 在移动端显示 1 像素的边框

## 简述

通过 CSS 设置的 1px 的边框，在移动端会显示为 2 像素的宽度，这里提供一种技巧，采用 CSS3 的缩放来实现。

对于为什么在移动端会显示为 2 像素（有的是 3 像素）的宽度，请查看这篇文章：

[理解PC端和移动端的基本像素单位](/docs/pc_mobile_pixel_unit.md)

本例中，以 dpr 为 2 的屏幕（即 ppi 小于 480 的移动设备）为例，如果要同时兼容 dpr 为 3 的屏幕，那么可以通过 js 来选择需要缩放的比例。这里只讲 CSS 的实现。

## HTML

```html
<!--使用 border 为 1px 的样式-->
<div class="btn btn-1">test button 1</div>
<!--使用 scalc 缩放后的样式-->
<div class="btn btn-2">test button 2</div>
```

## CSS

```css
.btn {
	display: block;
	width: 80%;
	height: 60px;
	line-height: 60px;
	margin: 0 auto;
	box-sizing: border-box; /*注意此处使用非标准盒模型，即 width = content + padding + border*/
	background-color: #FFF68F;
	text-align: center;
	font-size: 24px;
}
```

对于 button 1，使用 `border: 1px solid #000` ：

```css
.btn-1 {
	border: 1px solid #000;
	border-radius: 8px;
}
```

对于 button 2，使用缩放的方法：


```css
.btn-2 {
	position: relative;
	border-radius: 8px;
}

.btn-2::after {
	content: ' ';
	width: 200%;
	height: 200%;
	position: absolute;
	top: -50%;
	left: -50%;
	box-sizing: border-box; /*注意此处使用非标准盒模型，即 width = content + padding + border*/
	border: 1px solid #000;
	border-radius: 16px;
	transform: scale(0.5);
	pointer-events: none;
}
```

## 思路

对原来的 button 不设置 border 值，并为其添加一个 after 伪类，并对其样式进行 0.5 倍的缩放，把这个 after 的样式覆盖到 button 样式上，下面对代码做一些拆解说明：

```css
.btn-2 {
	position: relative; /* 为了给 after 做定位参照 */
	border-radius: 8px;
}
```

```css
.btn-2::after {
  	width: 200%; /*两倍的宽*/
	height: 200%; /*两倍的高*/
    border-radius: 16px; /*两倍的边角圆度*/
    border: 1px solid #000; /*对于移动端的屏幕来说，这是两倍的像素*/
}
```

```css
.btn-2::after {
    /*缩放为 0.5 倍，因此以上的两倍属性都变成一倍的属性，需要注意的是，我们也将 border 的宽度也缩小了一倍*/
	transform: scale(0.5);
}	
```

```css
/*通过缩放为 0.5 倍，它的 absolute 定位也相对自身做了 50% 的偏移，因此需要通过 -50% 的左右距离来做平衡*/
.btn-2::after {
	position: absolute;
	top: -50%;
	left: -50%;
}
```

```css
.btn-2::after {
    /*after 覆盖在 btn-2 的上面，会导致btn里面的内容无法点击，如 a 标签。因此，加上这个属性可以进行点击穿透*/
	pointer-events: none;
}
```

## Demo

demo 路径：`/example/1px_border_on_mobile`

##  查看效果

请点击链接：[点击这里](https://wengyifeng-hl.github.io/css-cookbook/example/1px_border_on_mobile/index.html)

或扫描以下二维码查看在移动端显示的效果：

![移动端查看效果](../resources/1px_border_on_mobile/1px_border_on_mobile.png)

