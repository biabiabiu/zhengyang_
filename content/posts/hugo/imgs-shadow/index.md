---
title: "Hugo图片添加阴影和圆角"
description:  "Hugo中为图片添加阴影"
keywords: ["hugo","图片阴影"]

date: 2022-02-20T20:18:53+08:00
draft: false

tags: ["Hugo","Hugo配置"]
categories: ["学习"]
---



为文章的图片添加阴影和圆角效果。

<!--more-->

博客基于`Hugo`搭建，主题是`LoveIt`

主题自身并没有对图片进行美化，原始的样式

<center>
    <img src="/images/still-image/limei.png" title="石原里美" alt="图片" height="100%" />
</center>

之前写作是在微信公众号，配合`壹伴`插件，也能对图片进行美化，设置圆角和阴影等等。看起来挺舒服的

用`开发者工具`查看其样式，直接照搬

```css
.imgShadow {
    box-shadow:rgb(210, 210, 210) 0em 0em 0.5em 0px;
    border-radius:6px;
}
```

在Hugo根目录`assets`下新建`/assets/css/_custom.scss`样式文件

```css
// ==============================
// Custom style
// 自定义样式
// ==============================
// 公众号文章图片阴影和圆角
.jf-image-shadow {
	box-shadow:rgb(210, 210, 210) 0em 0em 0.5em 0px;
	border-radius:6px;
}
```

之后在写文章时再进行引用

```html
<center>
    <img class="jf-image-shadow" src="/images/still-image/limei.png" title="石原里美" alt="图片-石原里美" height="100%" />
</center>
```

效果如下

<center>
    <img class="jf-image-shadow" src="/images/still-image/limei.png" title="石原里美" alt="图片-石原里美" height="100%" />
</center>

