# 在移动端显示 1px 的线

## 简述

在 PC 端编写的 1px 的线条或者边框，因视口对于关系，在移动端表现出来都是 2px。如果 UI 设计的线条颜色是很浅的，那么不会有太大影响，但对于深色的线条，2px 和 1px 的差别还是非常明显的。这里提供一种技巧来使线条在移动端也表现出 1px 的高度。

## 例子

HTML code:

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

CSS code:

```css
.title-1 {
	border-bottom: 1px solid #000;
}

.title-2 {
	position: relative;
}
.title-2:after {
	content: '';
	display: block;
	position: absolute;
	bottom:0;
	left:0;
	width: 100%;
	border-bottom: 1px solid #000;
	transform: scaleY(0.5);
}
```

演示效果：[点击这里](https://jsfiddle.net/wengyifeng/h4p4ts57/)