---
title: "文章内容增加版权声明"
description:  "为我的博客文章内容增加版权声明"
keywords: ["Hugo","版权声明"]

date: 2022-02-14T00:56:45+08:00
draft: false

tags: ["Hugo","Hugo配置"]
categories: ["Hugo"]
---



为我的原创文章增加版权声明。

<!--more-->

#### 前言

因为本人没有系统地学习过前端知识，所以在搭建此博客后进行页面美化以及配置时有些费力，只能去翻看前辈的总结概述，照葫芦画瓢

关于增加版权声明这里，找了许久没有发现能借鉴来的经验(个人能力有限)

笨人用笨方法，这里的解决办法，并不是值得学习的案例...

#### 困难

对于我，还是挺有难度的...

1. 我的内容有个人原创，也有搬运和截取的片段等，但不会使用代码进行逻辑判断
2. 不会使用模板语言等对页面模板进行修改，再增加`CSS`等的方式进行页面渲染
3. 复杂的页面看不懂，不过简单的`HTML`和`CSS`可以看懂一点点

#### 解决方法

在`开发者工具`中模仿前辈的版权声明，用简单的`HTML`和简单的`行内样式`进行页面渲染

刚好在`google search`中提交站点地图`sitemap.xml`时遇到状态显示`无法读取`的问题，去搜索解决方法的时候，看到了这位前辈的一篇报错处理：[谷歌 sitemap.xml 报错解决：无法读取此站点地图](https://last2win.com/2020/03/10/google-error/)

他的文档最后就有版权声明，是我喜欢的类型😁

#### 具体操作

`在开发者工具`中找到对应的`标签元素`，便是下面的内容

```html
<!--修改前-->
<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#deebf7">
    <h3>文档信息</h3>
    <ul>
        <li>本文作者：<a href="https://last2win.com" target="_blank">last2win</a></li>
        <li>本文链接：<a href="https://last2win.com/2020/03/10/google-error/" target="_blank">https://last2win.com/2020/03/10/google-error/</a></li>
        <li>版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
    </ul>
</div>
```

渲染出的效果如下：

<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#deebf7"><h3>文档信息</h3><ul><li>本文作者：<a href="https://last2win.com" target="_blank">last2win</a></li><li>本文链接：<a href="https://last2win.com/2020/03/10/google-error/" target="_blank">https://last2win.com/2020/03/10/google-error/</a></li><li>版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li></ul></div>

如果亲自去查看前辈的效果，不难发现这里的会比较丑...

除了需要更改链接内容外，还需要在几个标签上简单优化

- 扩大内边距`padding-top`和`padding-bottom`
- 修改背景颜色为`#f7f7f7`使其与我的页面背景更搭

```html
<!--修改后-->
<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#f7f7f7">
    <h3>文档信息</h3>
    <ul style="padding-bottom:1.5em;">
        <li style="padding-top:0.5em;">本文作者：<a href="https://zhengyang.wang/" target="_blank">正阳</a></li>
        <li style="padding-top:0.5em;">本文链接：<a href="https://zhengyang.wang/add-copyright-notice" target="_blank">https://zhengyang.wang/add-copyright-notice</a></li>
        <li style="padding-top:0.5em;">版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
    </ul>
</div>
```

于是，便有了下面的效果

<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#f7f7f7">
    <h3>文档信息</h3>
    <ul style="padding-bottom:1.5em;">
        <li style="padding-top:0.5em;">本文作者：<a href="https://zhengyang.wang/" target="_blank">正阳</a></li>
        <li style="padding-top:0.5em;">本文链接：<a href="https://zhengyang.wang/add-copyright-notice" target="_blank">https://zhengyang.wang/add-copyright-notice</a></li>
        <li style="padding-top:0.5em;">版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
    </ul>
</div>