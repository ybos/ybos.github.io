---
title: 通过 Hexo 在 Github Pages 上写博客
tags: [Github,Hexo,Github Pages,Node.js]
date: 2018-02-09 16:24:00
categories: github
---
# 通过 Hexo 在 Github Pages 上写博客

### Github Pages 简介
Github Pages 是通过 Github 托管并发布的公开网页。
一切都是美好的，但是有可能会被墙... =。=

### 前期准备
#### Github
创建一个仓库名称为 `账户.github.io` 的仓库
下载 Git 相关客户端，任选其一即可，详细的使用方法可以自行查询：
1. [SourceTree](https://www.sourcetreeapp.com/)
2. [Github客户端](https://desktop.github.com/)
3. [Git官方客户端](https://git-scm.com/downloads)

#### Node.js
在官网上下载 Node.js 的安装包，并安装[下载 Node.js 的官网地址](https://nodejs.org/en/)

#### Hexo
打开 CMD 或者 Terminal 运行命令安装 Hexo
```
$ npm install hexo -g
```
安装成功之后，运行命令查看 Hexo 是否安装成功
```
$ hexo -v
```

### 使用 Hexo
1. 创建一个新的目录用于初始化 Hexo 所有的资源，初始化的时候需要等待一段时间
```
$ mkdir hexo
$ cd hexo
$ hexo init # 这一步需要等待一段时间
$ npm install # 这里安装所有 Hexo 需要用到的组件
```
2. 生成资源
```
$ hexo generate
```
3. 部署本地服务，通过 [http://localhost:4000](http://localhost:4000) 访问 Hexo 博客
```
$ hexo server
```
4. 如果端口被占用可以通过 -p 来改变端口号
```
$ hexo server -p 6969
```

### 使用 Hexo 来生成 Github Pages 的内容
因为 Github Pages 只能通过静态文件来访问，故而需要由 Hexo 来生成相应的内容
1. 使用 Git 相应客户端把刚刚创建的 `git@github.com:账户/账户.github.io.git` Clone 下来
2. 将 hexo 目录内的全部文件拷贝入 `账户.github.io.git` 目录内
3. 修改项目内的 `_config.yml` 文件，在文件的底部编辑 deploy 块，注意填写的 repository `是 https格式的，而非 SSH 格式`
```
deploy:
    type: git
    repository: https://github.com/账户/账户.github.io.git
    branch: master
```
4. 使用 CMD / Terminal 进入 `账户.github.io.git` 目录内，并执行部署操作
```
$ hexo clean
$ hexo generate
$ hexo deploy
```
加入在执行 `hexo deploy` 命令时提示 `ERROR Deployer not found: git` 则需要运行命令安装依赖包
```
$ npm install hexo-deployer-git --save
```
安装依赖包完成后重新执行命令 `hexo deploy`

这样一来，已经把博客发布到 Github Pages 上了，可以打开你的博客地址查看内容了
博客地址就是刚刚你的仓库名，像我的就是：[ybos.github.io](ybos.github.io)

### 如何写博客
Hexo 使用 Markdown 作为博客载体，所以你可以使用你所熟悉的 Markdown 工具来撰写博客。
将 .md 文件放在 `/source/_posts` 内，重新执行命令即可访问
```
$ hexo clean
$ hexo generate
```
推荐几个常用的工具：
1. [马克飞象](https://maxiang.io/) for Web
2. [Mou](http://25.io/mou/) for Mac

### 选择主题皮肤
将你喜欢的主题下载下来，放在 themes 中，修改 _config.yml 中的 theme 为目录名重新生成即可

### 后续
如果在使用中发现什么问题，可以在 [我的 Github](https://github.com/ybos/ybos.github.io) 中提 issue，我的 Github 仓库地址 [https://github.com/ybos/ybos.github.io](https://github.com/ybos/ybos.github.io)