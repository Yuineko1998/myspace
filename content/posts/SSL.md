---
date: "2021-11-18T10:33:00+08:00"
description: 白嫖一份SSL证书
draft: false
tags:
- Hugo
- SSL证书
title: Hugo|给博客安装SSL安全证书
---

## 1.起因

打算给博客换上`diary` 主题，本地预览成功，在推送到github后却发现网站的CSS无法渲染，按`F12`查看网页报错，发现显示网站不可信任，需要安装SSL证书。

> SSL 证书是一个数字证书，用于认证网站的身份并启用加密连接。 SSL 代表安全套接字层，这是一个安全协议，可在Web 服务器和Web 浏览器之间创建加密链接。

## 2.开工

1.邮箱注册：[Let's Encrypt](https://easy.zhetao.com/)

2.点击左上角的添加域名，输入域名后创建域名，然后点创建证书，输入域名。

![image-20211118101113581](https://i.loli.net/2021/11/18/c4MGZA62xKbNW3g.png)

3.添加DNS域名解析。

Let's Encrypt 会推荐几种验证方式。

> **DNS验证**：通过添加DNS解析记录验证域名。验证方式将在生成时动态提示操作方法。
>
> **HTTP验证**：如果下面添加的域名均可通过HTTP(80端口)访问（推荐，如果你的网站服务器可配置跳转(URL Rewrite)，还可自动更新证书）;
>
> **推荐方式**：如果你具有域名的解析权限，建议使用DNS验证，只需要为每一个（子）域名添加一条NS记录，即可自动生成和续期证书。

我的域名是在[Dynadot](https://www.dynadot.com/zh/)购买，14块钱买了一年，可以在托管网站进行DNS验证。在我的域名->域名管理->找到对应域名->DNS设置。

需要在DNS设置中，添加一条TXT记录和一条NS或CNAME记录，由于[Dynadot](https://www.dynadot.com/zh/)不支持NS记录，所以选择后者。子域名不用带上自己的域名和后缀，填网站提供的那两个就行。

![image-20211118102546612](https://i.loli.net/2021/11/18/IGxg1wr9fDzLniH.png)

一般15min以后生效。

4.回到Let's Encrypt的证书管理页面，验证即可。

