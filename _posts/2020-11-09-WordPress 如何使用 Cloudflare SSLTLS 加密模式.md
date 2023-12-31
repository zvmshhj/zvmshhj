﻿---
layout: post
title:  "WordPress 如何使用 Cloudflare SSL/TLS 加密模式"
date:   2020-11-09-12:20:50
categories: ML
tags: Margin
excerpt: 这里需要注意的是，通过 Cloudflare 申请证书为泛域名证书，同个域名都可以使用，包括但不限于 www 这样的二级域名。KEY 私钥文件需要自己保管好，PEM 文件可以在 Cloudflare 源服务器处下载（如下图右下角所示）。 首...
mathjax: true
---
这里需要注意的是，通过 Cloudflare 申请证书为泛域名证书，同个域名都可以使用，包括但不限于 www 这样的二级域名。KEY 私钥文件需要自己保管好，PEM 文件可以在 Cloudflare 源服务器处下载（如下图右下角所示）。

首先登陆 Cloudflare 账号，进入对应域名，依次点击SSL/TLS→源服务器→创建证书，如下图所示
![](https://vi0.xiu123.cn/live/2020/11/09/17/1003v1604915394760436725.jpg)

通过 Cloudflare 申请泛域名证书，并下载保存 KEY 和 PEM 文件。
部署服务器 SSL 证书
将下载好的文件直接上传到服务器对应目录下，使用控制面板的小伙伴，使用文本编辑软件打开（或者直接申请的时候就复制保存好），粘贴到对应区域进行保存生效。这里 WPEXP 以宝塔控制面板为例：
![](https://vi3.xiu123.cn/live/2020/11/09/17/1003v1604915429984495100.jpg)

使用宝塔控制面板可以轻松部署网站 SSL 证书。
由于可以通过 Cloudflare 强制 HTTPS 访问，所以不要开启宝塔 SSL 控制台右上角的强制 HTTPS按钮，否则会导致跳转次数过多的错误提示。
![](https://vi0.xiu123.cn/live/2020/11/09/17/1003v1604915488848186195.jpg)




开启强制 HTTPS 访问
等源服务器部署 SSL 证书之后，回到 Cloudflare SSL/TLS 概述界面，如下图所示：
通过 Cloudflare 设置强制使用 HTTPS 访问网站。
Cloudflare 的默认 SSL/TLS 加密模式为灵活，这里建议改成完全（严格），如果是博客类、技术类网站，建议使用更安全的 TLS 模式；如果是门户类、商城类网站，则不建议开启 TLS 模式，以增加访问的兼容性。
至此，你的网站小绿锁就出现了，完美的解决了站点 SSL 加密，使用 HTTPS 访问。不但增加安全性，而且更加有利于搜索引擎，更适合 SEO 优化。
