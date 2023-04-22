---
title: "Hugo生成文章摘要的几种方式"
description:  "Hugo生成文章摘要的几种方式以及注意事项"
keywords: ["Hugo","文章摘要","summary"]
summary: "Hugo生成文章摘要的几种方式以及注意事项"

date: 2023-04-22T00:25:25+08:00
draft: false

tags: ["Hugo","记录"]
categories: ["学习"]
---

摘要是一篇文章的灵魂

读者可以大致了解整篇的表述，来判断是否有继续读下去的必要

# 内容摘要

Hugo支持内容摘要的生成，生成的摘要可以使用`.Summary`变量调用

生成的摘要将呈现在首页的文章标题下，并自动增加`阅读更多`的按钮来指向整篇内容

## 生成方式

- 自动生成
- 手动生成
- 前置参数生成

### 自动生成

默认情况下, Hugo 自动将内容的**前 70 个单词**作为摘要

可以通过修改配置文件中的`summaryLength`来自定义摘要的长度，例如修改为前120

> #### summaryLength 
>
> **Default value:** 70
>
> The length of text in words to show in a `.Summary`.
>
> [ Configure Hugo | Hugo ](https://gohugo.io/getting-started/configuration/#summarylength)

```toml
summaryLength = 120
```

{{< admonition type=tip title="提示" open=true >}}

尽管summary中支持HTML标签等元素，但是并不建议，这样可能会导致渲染错误

 {{< /admonition >}}

### 手动生成

摘要生成还可以通过在文章的开始部分增加标签来实现`< !--more-- >`

```markdown
这是段落1
这是段落2
< !--more-- >
以下是正文部分...
```

`< !--more-- >`标签之前的内容将作为摘要部分，效果与**自动生成**相同

相比较于**自动生成**，可能需要额外增加一些内容来充当摘要部分

{{< admonition type=tip title="提示" open=true >}}

由于渲染的问题，文中出现的所有`< !--more-- >`标签的`<`和`>`都添加了一个空格

正确写法请到[Content Summaries |Manual Summary Splitting](https://gohugo.io/content-management/summaries/#manual-summary-splitting)查看

 {{< /admonition >}}

### 前置参数生成

Hugo支持在文章的`Front Matter`中添加`summary`变量来单独设置摘要

```toml
title: "文章标题"
summary: "这是文章的摘要部分"
```

Hugo将会把`summary`中的内容渲染为文章摘要，效果与**自动生成、手动生成**相同

相较于**自动生成和手动生成**，仍然需要额外增加内容，但是可以选择不再文章中体现，以实现摘要与文章分离

### 优先级

因为同时支持多种方式生成，Hugo给出了摘要生成的优先级顺序：

`Front Matter` > `手动生成` > `自动生成`

若同时出现两种以上，则以前者为优先拆分摘要



{{< admonition type=tip title="参考链接" open=true >}}

[Content Summaries | Hugo (gohugo.io)](https://gohugo.io/content-management/summaries/)

 {{< /admonition >}}

