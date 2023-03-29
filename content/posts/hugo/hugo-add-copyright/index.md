---
title: "Hugo文章添加版权声明"
description:  "介绍了我是如何在文章中添加版权声明的"
keywords: ["版权声明","Hugo"]

date: 2023-03-29T11:33:00+08:00
draft: false

tags: ["Hugo"]
categories: ["学习"]
---

这篇介绍了我是如何在文章中添加版权声明的

<!--more-->

最初部署站点时没有考虑过设置版权声明，本着互联网精神的核心是“共享”，如果可以为大家提供些许帮助或值得借鉴的内容，对我来说是非常荣幸的

公众号上遇到一篇非常不错的文章，作者希望每位创作者要有版权意识，尊重其他创作者版权的同时，也倡导为自己的作品添加“版权声明”，**表明自己对该作品拥有版权，不能随意转载等**

觉得是非常不错的建议，于是便借鉴了一些前辈文章版权声明的样式

#### 旧方案

由于没有系统地学习开发相关的知识，当时对于Hugo完全不懂，博客是跟着一些前辈的文章教程逐步搭建部署，也没有查到关于`Hugo如何添加版权声明`的相关介绍

在看了Hugo的文档后晓得`archetypes`可以放置文档模板，于是就在`archetypes`下加了一个`default.md`，并把copy来的样式模板加了进去

这是我之前的方法——[为文章内容添加版权声明](https://zhengyang.wang/2022/02/add-copyright-notice/)

以自己对Hugo的理解，只想到了这个土方法😂

```html
<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#f7f7f7">
    <h3>文档信息</h3>
    <ul style="padding-bottom:1.5em;">
        <li style="padding-top:0.5em;">本文作者：<a href="https://zhengyang.wang/" target="_blank">正阳</a></li>
        <li style="padding-top:0.5em;">本文链接：<a href="https://zhengyang.wang/oneplus-removes-dual-storage/" target="_blank">https://zhengyang.wang/oneplus-removes-dual-storage</a></li>
        <li style="padding-top:0.5em;">版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
 </ul>
</div>
```

<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#f7f7f7">
    <h3>文档信息</h3>
    <ul style="padding-bottom:1.5em;">
        <li style="padding-top:0.5em;">本文作者：<a href="https://zhengyang.wang/" target="_blank">正阳</a></li>
        <li style="padding-top:0.5em;">本文链接：<a href="https://zhengyang.wang/oneplus-removes-dual-storage/" target="_blank">https://zhengyang.wang/oneplus-removes-dual-storage</a></li>
        <li style="padding-top:0.5em;">版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
 </ul>
</div>


以及这样的

```html
<div style="margin-top:2em;padding:0 0.5em;font-size:.875rem">
    <hr>
    <div style="padding-bottom:1em;">
        <p>本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></p>
        <p>本文链接：<a href="https://zhengyang.wang/linux-config-clash/" target="_blank">https://zhengyang.wang/linux-config-clash</a></p>
        <p>版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</p>
    </div>
</div>
```

<div style="margin-top:2em;padding:0 0.5em;font-size:.875rem">
    <hr>
    <div style="padding-bottom:1em;">
        <p>本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></p>
        <p>本文链接：<a href="https://zhengyang.wang/linux-config-clash/" target="_blank">https://zhengyang.wang/linux-config-clash</a></p>
        <p>版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</p>
    </div>
</div>

后面再`new posts`新增文章时，末尾都会有版权声明的样式

但麻烦的是每次都需要对样式中的链接以及链接文本进行修改，而且后续若要更换样式，也要将所有的文档逐个修改

#### 新的解决方案

在对Hugo有了一定了解后，知道可以直接修改模板文件

例如我用的主题是`LoveIt`，就将目录`/themes/LoveIt/layouts/posts/single.html`复制到根目录`/layouts/posts/single.html`

在`{{- /* Content */ -}}`下添加了以下内容，其中`.Permalink`变量可以获得当前文章的链接，`.Title`获取当前文章的标题

```html
{{- /* Content */ -}}
<div class="content" id="content">
    {{- dict "Content" .Content "Ruby" $params.ruby "Fraction" $params.fraction "Fontawesome" $params.fontawesome | partial "function/content.html" | safeHTML -}}
    <!-- 添加文章版权声明信息 -->
    <div style="margin-top:2em;padding:0 0.5em;font-size:.875rem">
        <hr>
        <div style="padding-bottom:1em;">
            <p>本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></p>
            <p>本文链接：<a href="{{ .Permalink }}" target="_blank">{{ .Title }}</a></p>
            <p>版权声明：<a href="https://creativecommons.org/licenses/by-nc/4.0/" target="_blank">「署名-非商业性使用-相同方式共享 4.0 国际」</a></p>
        </div>
    </div>
</div>
```

渲染后的效果是这样的

<div style="margin-top:2em;padding:0 0.5em;font-size:.875rem">
                <hr>
                <div style="padding-bottom:1em;">
                    <p>本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></p>
                    <p>本文链接：<a href="https://zhengyang.wang/2023/03/useful-microsoftedge/" target="_blank">浏览器，我选择MicrosoftEdge</a></p>
                    <p>版权声明：<a href="https://creativecommons.org/licenses/by-nc/4.0/" target="_blank">「署名-非商业性使用-相同方式共享 4.0 国际」</a></p>
                </div>
            </div>



将之前文章中的旧样式逐个删去，再次生成站点时则会将新样式渲染进页面

后面就不需要在新增文章时手动添加了，如果需要更换样式，直接更换`single.html`里面的内容即可

遗憾的是当时copy来的样式来源信息找不到了...

以上