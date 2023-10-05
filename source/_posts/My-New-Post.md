---
title: Github.io + Hexo + Aurora 主题搭建个人博客
date: 2023-10-05 20:51:36
tags: 博客
---

# Github.io + Hexo + Aurora 主题搭建个人博客

## 通过 github.io 创建个人页面
### 登录 github 创建仓库
因为我们创建的是个人页面仓库，所以仓库的名称以 username.github.io 为命名，其中 username 是你的 github 账户的用户名，因为每个账号只能创建一个 github.io 页面，所以 username 写其他的名称不会生效

![创建仓库](https://lengyuerbucket.oss-cn-beijing.aliyuncs.com/blog/create.jpg)

其他配置：
![其他配置](https://lengyuerbucket.oss-cn-beijing.aliyuncs.com/blog/setting.jpg)

创建完仓库之后在长裤里面的 docs 目录下创建 index.html 文件就会，访问你的 github.io 地址就会解析到这个这个 html 进行页面展示了


## 使用 hexo 生成页面
因为我们的网站手动写 html 比较麻烦，不如使用 markdown 的方式去生成页面会比较方面，因为我们程序员记笔记也是 markdown 风。
这时候既能解析 markdown 文章又能生成对应美观可定制的页面的需求非 hexo 框架去做了。

1. 首先全局安装 hexo
```javascript
$ npm install -g hexo-cli
```
2. 生成博客项目
```javascript
$ hexo init <folder>
$ cd <folder>
$ npm install
```

此时就已经安装好了对应的博客，但是主题是默认的不是很好看～

## 安装 aurora 主题生成页面并发布
安装一个好看的主题 aurora

1. 安装主题及插件
```
$ npm install hexo-theme-aurora hexo-plugin-aurora --save
```

2. 生成主题配置 _config.aurora.yml
```
$ touch _config.aurora.yml
```

此时 `_config.aurora.yml` 是一个空文件，我们把默认配置复制进去既 https://github.com/auroral-ui/hexo-theme-aurora/blob/main/_config.yml 里面的内容。

3. 修改 _config.yml 主题
```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: aurora
```

4. 设置 permalink
打开在 Hexo 根目录下的 _config.yml, 修改 permalink 参数为 /post/:title.html

```
# URL
## Set your site url here. For example, if you use GitHub Page, set url as 'https://username.github.io/project'
url: https://tridiamond.tech
permalink: /post/:title.html
permalink_defaults:
pretty_urls:
  trailing_index: true # Set to false to remove trailing 'index.html' from permalinks
  trailing_html: true # Set to false to remove trailing '.html' from permalinks
```

5. 生成界面并运行
```
$ hexo clean & hexo g & hexo server
```
访问本地地址 localhost:4000 就能看到当前的默认主题博客了。

### 配置上传 github 部署博客
1. 配置页面产出目录为 docs 
![配置 publish](https://lengyuerbucket.oss-cn-beijing.aliyuncs.com/blog/setting_publish.jpg)

2. 清除当前的产出页面并再次生成
```
$ hexo cl && hexo g
```

3. 把当前的代码提交到代码仓库
把当前的代码提交到仓库之后，过一会页面就会更新成我们的主题页面了～