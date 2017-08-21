# 多行文本省略

## 简述

要求在某一区域显示多行文字，若超过规定的行数，那么将最后一行接近末尾的文字截断，且截断部分用省略号表示。

## 例子

HTML code:

```html
<div class="container">
  <span class="brief-info">
    层叠样式表(英文全称：Cascading Style Sheets)是一种用来表现HTML（标准通用标记语言的一个应用）
    或XML（标准通用标记语言的一个子集等文件样式的计算机语言。
    CSS不仅可以静态地修饰网页，还可以配合各种脚本语言动态地对网页各元素进行格式化。
  </span>
</div>
```

CSS code:

```css
.brief-info {
  display: -webkit-box;	
  width: 430px;
  overflow: hidden;
  text-overflow: ellipsis;
  -webkit-line-clamp: 3; /*超过三行则省略*/
  -webkit-box-orient: vertical;
}
```

效果演示：[点击这里](https://jsfiddle.net/wengyifeng/yf4xu3ar/)

## 说明

### 核心属性

+ -webkit-line-clamp [ CSS3 ]
+ -webkit-box-orient [ CSS3 ]

### 核心属性值

+ display : -webkit-box [ CSS3 ]

### 思路

（待补充）

## 补充

可添加 `  text-align: justify;` 来进行对齐。

```css
.brief-info {
  display: -webkit-box;	
  width: 430px;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
  text-align: justify; /*添加的内容*/
}

```

 