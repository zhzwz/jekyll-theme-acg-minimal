---
title: Jekyll Theme ACG 主题使用指南
description: 介绍如何从零开始配置 Jekyll Theme ACG 主题。
categories: ["Jekyll Theme ACG"]
tags: ["guide", "chinese"]
---

## 快速开始

### 依赖环境

- ruby 2.7
- bundle 2.2
- jekyll 4.2

### 手动安装

- Fork 项目 [jekyll-theme-acg-minimal](https://coderzhaoziwei.github.io/jekyll-theme-acg-minimal)

- 执行命令 `bundle update && bundle exec jekyll serve -o` 开始本地测试

### 自动部署

每当分支 `main` 有 `push` 操作，GitHub Actions 会执行 `.github/workflows/deploy.yml` 文件内容，在分支 `github-pages` 上发布站点内容。

别忘记配置 Github 项目仓库的相关设置，如下图。

![](/assets/images/2021-07-03-settings-pages.png)

## 全局配置

全局配置存放于配置文件 `_config.yml` 中。

```yml
url:                    # 站点地址
baseurl:                # 站点路径，默认值 `/`
title:                  # 站点名称
description:            # 站点描述
author:                 # 作者名称，目前仅用于在页脚中显示。
lang:                   # 站点语言，默认值 `en-US`

theme: jekyll-theme-acg # 主题名称

# 主题属性
acg:
  color:                # 主题颜色，默认值 `red`
  background:           # 主题背景，默认值 `https://cdn.jsdelivr.net/gh/coderzhaoziwei/jekyll-theme-acg/assets/images/pixiv86925095.png`
  categories:
    label:              # 分类名称，默认值 `Categories`
    description:        # 分类描述
  tags:
    label:              # 标签名称，默认值 `Tags`
    description:        # 标签描述
  about:
    label:              # 关于名称，默认值 `About`
    description:        # 关于描述
  friends:
    label:              # 友链名称，默认值 `Friends`
    description:        # 友链描述
  error:
    label:              # 错误名称，默认值 `404`
    description:        # 错误描述，默认值 `Page not found.`

# 需要被排除的文件列表
exclude: [
  "LICENSE",
  "README.md",
  "package.json",
]

# Jekyll Theme ACG 主题的必要配置
# 如果你不了解下面这些值的意义，那么请不要随意改动。
defaults:
- scope:
    path: ""
  values:
    layout: page
- scope:
    path: "index.html"
  values:
    layout: page
    type: home
- scope:
    path: ""
    type: posts
  values:
    layout: page
    permalink: /posts/:title
    type: post
```

### baseurl

只有当站点路径是域名下的子路径时，才必须要设置。

例如：`https://coderzhaoziwei.github.io/jekyll-theme-acg-minimal` 的站点路径是域名下的子路径，只有配置 `baseurl: /jekyll-theme-acg-minimal` 才可以正常使用。

### acg.color

主题色可以在以下这些值中选择：

- red
- blue
- green
- yellow
- pink
- purple
- gray

### acg.background

背景可以是外部链接，也可以是本站路径。

例如：`background: /assets/bg/example.png`

## 文章配置

文章存放于 `_posts` 文件夹中，文件名建议按照 `YYYY-MM-DD-title.md` 的格式。

每篇文章都必须在开头使用 YAML 格式的 Front Matter，Front Matter 会使文件被 Jekyll 识别为特殊文件，Front Matter 的内容将会被绑定为这篇文章的独有属性。

```
---
title:
description:
categories: []
tags: []
lang:
color:
background:
pin:
---
```

### title（必要）

文章的标题。

如果没有手动设置 title 值，那么 Jekyll 将会使用文件名生成一个 title 值。假如有一篇文章的文件名是 `2021-06-01-show-rendering-cn.md`，那么自动生成的标题为 `Show Rendering Cn`，通常应该避免这种情况。

### description

文章的简述。

如果没有手动设置 description 的值，那么 Jekyll 将会自动提取文章的开头生成一个 description 值。

### categories

文章的分类。推荐使用数组的形式。

```
---
categories: ["分类一", "分类二", "分类三", "可 以 空 格"] # 分类名中可以使用空格
categories: 分类一 分类二 分类三 # 空格用于隔开，分类名中不能使用空格
---
```

### tags

文章的标签。基本规则与 `categories` 相同。

### color

文章的主题色。

如果没有手动设置 `color` 的值，那么 Jekyll 将会读取全局配置 `_config.yml` 中的 `color` 值。

### background

文章背景图片。

如果没有手动设置 `background` 的值，那么 Jekyll 将会读取全局配置 `_config.yml` 中的 `background` 值。

### pin

文章置顶选项。

如果 `pin` 的值不是 `true`，那么本篇文章就不会在首页置顶。
