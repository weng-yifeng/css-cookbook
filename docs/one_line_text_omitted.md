# 一行文本省略

## 简述

仅要求在某一区域显示一段文字，若句子超过规定的宽度，那么将该句子截断，且截断部分用省略号表示。

## 例子

HTML code:

```html
<div class="container">
  <span class="brief-info">
    层叠样式表(英文全称：Cascading Style Sheets)是一种用来表现HTML（标准通用标记语言的一个应用）
    或XML（标准通用标记语言的一个子集等文件样式的计算机语言。
  </span>
</div>
```

CSS code:

```css
.brief-info {
  display: inline-block;
  width: 430px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

效果演示：[点击这里](https://jsfiddle.net/wengyifeng/zeaqd6hv/1/)

## 说明

### 核心属性

+ text-overflow [ CSS3 ]
+ white-space [ CSS1 ]

### 思路

在固定的宽度下，首先使用 white-space 属性让文字不换行，再设置 overflow 把超出宽度的部分给隐藏起来，最后结合 text-overflow 属性，设置隐藏部分的样式用省略号来表示。

另外，因 span 标签是行内元素，为了让其样式可以修改，所以这里修改为行内块元素（ display : inline-block ）。