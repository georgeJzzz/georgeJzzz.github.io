---
title: hexo+github+域名
date: 2022-03-08 13:14:35
index_img: https://rmt.dogedoge.com/fetch/fluid/storage/actions-deploy/cover.png?w=480&fmt=webp
tags: 
- hexo
- 域名
- github
categories:
  -hexo部署
---

# 什么是 Hexo？

Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

## 安装

安装 Hexo 只需几分钟时间，若您在安装过程中遇到问题或无法找到解决方式，请 [提交问题](https://github.com/hexojs/hexo/issues)，我们会尽力解决您的问题。

## 安装前提

安装 Hexo 相当简单，只需要先安装下列应用程序即可：

-   [Node.js](http://nodejs.org/) (Node.js 版本需不低于 10.13，建议使用 Node.js 12.0 及以上版本)
-   [Git](http://git-scm.com/)

如果您的电脑中已经安装上述必备程序，那么恭喜您！你可以直接前往 [安装 Hexo](https://hexo.io/zh-cn/docs/#%E5%AE%89%E8%A3%85-Hexo) 步骤。

如果您的电脑中尚未安装所需要的程序，请根据以下安装指示完成安装。

# 使用

## 建站

```shell
$ hexo init <folder>
$ cd <folder>
$ npm install
```

新建完成后，指定文件夹的目录如下：
```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```


## 下载主题 Fluid 

### 主题介绍

Fluid 是基于 Hexo 的一款 Material Design 风格的主题，由 [Fluid-dev (opens new window)](https://github.com/fluid-dev) 负责开发与维护。

主题 GitHub: [https://github.com/fluid-dev/hexo-theme-fluid (opens new window)](https://github.com/fluid-dev/hexo-theme-fluid)

预览网站：[Fluid's blog (opens new window)](https://hexo.fluid-dev.com/) [zkqiang's blog (opens new window)](https://zkqiang.cn/)

Hexo 5.0.0 版本以上，推荐通过 npm 直接安装，进入博客目录执行命令：
> npm install --save hexo-theme-fluid

然后在博客目录下创建 _config.fluid.yml，将主题的 _config.yml (opens new window)内容复制过去
> 注意主题的_config.yml 是github里面的主题

_config.fluid.yml 在配置参考主题官网： https://hexo.fluid-dev.com/docs/start/#%E5%88%9B%E5%BB%BA%E3%80%8C%E5%85%B3%E4%BA%8E%E9%A1%B5%E3%80%8D

# 注意事项

## 绑定github

在 _config.yml 文件下配置
```
## Set your site url here. For example, if you use GitHub Page, set url as 'https://username.github.io/project'
url: http://blog.georgehoo.fun  // 修改这个域名地址， 没有配置域名请改变未github地址
```

在source文件下创建CNAME, 里面填写相关的域名
> georgehoo.fun


# 将 Hexo 部署到 GitHub Pages
参考地址： https://hexo.io/zh-cn/docs/github-pages
