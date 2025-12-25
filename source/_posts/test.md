---
author: zkc-dev
title: Pixiv 图片反向代理
date: 2022-10-03 14:47:33
category:
  - 教程
tags:
  - 代码
  - API
  - 娱乐
headimg: /posts/599ec3ed8eda/reverse_proxy_flow.png
references:
  - title: Pixiv 圖片代理
    url: https://pixiv.cat/reverseproxy.html
---

众所周知，Pixiv（以下简称 p 站）因各种不可抗力，在部分地区无法正常访问站点，并且图片服务器域名 `i.pximg.net` 具有盗链保护，只要 `Referer` 不是来自 p 站的请求，都会返回 403 状态码。那么，我们如何才能通过 URL 直接访问到图片资源？