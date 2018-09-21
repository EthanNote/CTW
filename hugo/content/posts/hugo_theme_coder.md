+++
draft = false
date = 2018-09-02T17:43:33+08:00
title = "Getting start with Coder theme"
slug = ""
tags = []
categories = []
+++

Coder主题十分简洁，基础功能健全，配置简单。

主题仓库中附带配置文件，拿来即可用。



### 问题及解决方法(Windows)

###### Post列表日期错误，且无法显示各post标题

检查 meta 是否含有多余空格。slug 配置所在行末尾有空格，导致解析错误。如果完全不需要slug，可以直接在 archetypes/posts.md 中将其删除

###### Hugo 版本不支持 x-scss

下载扩展板Hugo 

### 源代码语法高亮

```javascript
(function(){
    console.log("Hello, world!");
}).();

```
### 使用 highlightjs
```html
<pre><c>
(function(){
    console.log("Hello, world!");
}).();
</c></pre>
```

<pre><c>
(function(){
    console.log("Hello, world!");
}).();
</c></pre>



### English looks better

The default language is English, and it looks much more comfortable. Maybe it is a good idea to leave the most content to programming code. And you can see this text has an equal-width font, quite similar to console output, which is another cause of Chinese-hostile.



### Prefered configuration

- Build the site to hugo project root instead of 'public'.

- Base url can be overriden when debugging with 'hugo server' if -b parameter is given.

```bash
hugo server -d . -b localhost
```

### Disqus support

comment it out if not needed

```
#disqusShortname = "yourdiscussshortname" # Enable or disable Disqus.
```
