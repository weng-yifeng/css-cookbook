# 在移动端显示 1 像素的线

## 简述

在 PC 端编写的 1px 的线条或者边框，在移动端表现出来都是 2 像素或者 3 像素。如果 UI 设计的线条颜色是很浅的，那么不会有太大影响，但对于深色的线条，2 像素和 1像素的差别还是非常明显的。这里提供一种技巧来使线条在移动端也表现出 1 像素的厚度。

## 例子

HTML : 

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8" name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
	<title>css-cookbook</title>
	<link rel="stylesheet" type="text/css" href="./css-cookbook.css">
</head>
<body>
	
<h1 class="title-1">标题一</h1>
<h2 class="title-2">标题二</h2>
<div>
	<p>上面标题一的下划线就是直接写 1px 的效果。</p>
	<p>上面标题二的下划线就是缩小后的 1px 的效果。</p>
	<p>请在移动端查看效果。</p>
</div>

</body>
</html>
```

CSS : 

```css
.title-1 {
	border-bottom: 1px solid #000;
}

.title-2 {
	position: relative;
}
.title-2::after {
	content: '';
	display: block;
	position: absolute;
	bottom:0;
	left:0;
	width: 100%;
	border-bottom: 1px solid #000;
	transform: scaleY(0.5); /* Y 轴方向缩小为 0.5 倍 */
}
```

## 思路

原节点不设置下划线，而是通过 after 伪元素来设置，并对伪元素做 0.5 倍缩放处理，这样显示出来的线条在移动端即为 1 像素的厚度。

代码简析：

```css
.title-2 {
	position: relative; /* 作为伪类元素绝对定位的参照 */
}
.title-2::after {
	content: '';
	display: block;
	position: absolute; /* 绝对定位 */
	bottom:0; /* 固定到底部 */
	left:0;
	width: 100%; /* 和元素一样的宽度 */
	border-bottom: 1px solid #000;
	transform: scaleY(0.5); /* Y 轴方向缩小为 0.5 倍 */
}
```

## Demo

demo 路径：`/example/1pixel_line_on_mobile`

## 查看效果

请点击链接：[点击这里](https://wengyifeng-hl.github.io/css-cookbook/example/1pixel_line_on_mobile/index.html)

或扫描以下二维码查看在移动端显示的效果：

（待补充）

