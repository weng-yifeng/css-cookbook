# 行内元素布局技巧

## 简述

行内元素的布局会出现默认间距的问题，因此我们在布局的时候需要做几点属性设置。

## 例子

HTML code:

```html
<div class="card">
	
	<img class="head-pic" src="http://images.cnblogs.com/cnblogs_com/hlwyfeng/783931/o_mypic.jpg">

	<span class="self-intro">自我介绍</span>

	<div class="base-info">
		<span>名称：小翁</span>
		<span>住址：广东深圳</span>
	</div>
	
</div>

```

CSS code:

```css
.card {
	width: 600px;
	height: 300px;
	padding: 15px;
	background-color: #eee;
}

/*行内元素*/
.head-pic {
	height: 60%;
}

/*行内元素*/
.self-intro {
	display: inline-block;
	padding: 10px;
	border: 1px solid #7A67EE;
}

/*行内元素*/
.base-info {
	display: inline-block;
	padding: 10px;
	border: 1px solid #FF3030;
}

.base-info > span {
	display: block;
}
```

通过这样的布局，可以发现，行内元素之间会有一个默认的间距，同时行内元素并不会默认向顶部对齐。因此，可以通过添加以下属性来做调整，注意注释的部分：

```css

.card {
	width: 600px;
	height: 300px;
	padding: 15px;
	background-color: #eee;
	font-size: 0; /*消除行内元素的默认间距，也因此使子元素需要独自设置字体大小*/
}

/*行内元素*/
.head-pic {
	height: 60%;
}

/*行内元素*/
.self-intro {
	display: inline-block;
	padding: 10px;
	border: 1px solid #7A67EE;
	font-size: 14px; /*设置字体大小*/
	vertical-align: top; /*向顶部对齐*/
}

/*行内元素*/
.base-info {
	display: inline-block;
	padding: 10px;
	border: 1px solid #FF3030;
	font-size: 14px; /*设置字体大小*/
	vertical-align: top; /*向顶部对齐*/
}

.base-info > span {
	display: block;
}

```

效果演示：[点击这里](https://jsfiddle.net/wengyifeng/92t2o5pf/)

