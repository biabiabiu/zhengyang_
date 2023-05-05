---
title: "Hugo重新部署—本地覆盖远程仓库"
description:  "记录了重新部署Hugo的过程"
keywords: ["Hugo","部署"]
summary: "记录了我重新部署Hugo的过程"

date: 2023-04-05T11:33:12+08:00
draft: false

tags: ["Hugo"]
categories: ["学习"]
---



## 写在前面

使用过一段时间Hugo后，了解到直接修改主题源码是不好的习惯，不方面后续主题的更换或持续升级等操作

由于根目录的优先级高于themes/`THEME`/...，正确的做法应该是当有需要修改或新增的代码时，在根路径下创建相同结构的文件来覆盖，而不是直接修改主题源码

例如要修改`themes/LoveIt/layouts/partials/footer.html`时，就在`layouts/partials/`下新建`footer.html`文件来覆盖`theme`下的配置

刚使用Hugo搭建博客时，跟着教程逐步完成的，根路径和主题目录中被我修改的面目全非，新增的样式文件也是随意乱放。为了后续更好的使用，需要重新构建部署

## 构思

整个结构是比较混乱的。目的只是将博客的配置文件重新覆盖再修改，网站内容保持不变

- 保留`content`和`static`两个目录的文件

- `archetypes/default.md`有文章的前值参数

- `layouts`中有修改和新增的文件

- `assets`中有新增样式文件

- `theme/LoveIt/...`

  这里面就多了，还好自己修改源码时不忘添加备注...

- `new site`后对比旧的站点文件挨个修改

- 删改后再覆盖远程仓库，由于是部署在`Netlify`上的，尽量不对其产生影响

## 重新部署

内心是比较忐忑的，没查到相关的贴子，担心这个笨方法出现点差错，博客算是栽手里又要重新搭建部署。还好成功了！

以下为具体步骤

#### 新建站点

```bash
hugo new site NewMyWebSite
cd NewMyWebSite
git init
git submodule add https://github.com/dillonzq/LoveIt.git themes/LoveIt
```

#### 删改

把`LoveIt`下的`exampleSite`中的文件直接到复制到根目录下，然后将`config.toml`、`layouts`等文件对照着旧的配置进行修改和替换，并把`content/posts/`下的自带文章删掉

`theme`目录下的文件就不再变动了

这是一项麻烦的工作，需要细心地逐个查找既往配置文件是否有改动...

#### 覆盖远程仓库

1. 首先将远程仓库克隆一份进行备份
2. 将本地仓库(旧)中除了`.git`文件夹，其他全部删除
3. 将本地仓库(新)中除了`.git`文件夹，全部复制到旧仓库
4. `git add .`
5. `git commit -m "新的覆盖旧的"`
6. `git push`

这样可以实现覆盖，或者说是合并，但不是个专业的方案

