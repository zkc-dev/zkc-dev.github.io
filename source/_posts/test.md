---
author: zkc-dev
title: Redis 缓存优化
date: 2025-12-25 17:19:00
category:
  - 代码
tags:
  - 代码
  - Java
  - Redis
headimg: /posts/599ec3ed8eda/reverse_proxy_flow.png
references:
  - title: Pixiv 圖片代理
    url: https://pixiv.cat/reverseproxy.html
---

众所周知，Pixiv（以下简称 p 站）因各种不可抗力，在部分地区无法正常访问站点，并且图片服务器域名 `i.pximg.net` 具有盗链保护，只要 `Referer` 不是来自 p 站的请求，都会返回 403 状态码。那么，我们如何才能通过 URL 直接访问到图片资源？

## 优化前

| 线程数 | Ramp-up | 循环次数 | 平均延迟 | P99延迟 | 异常率 |
| ------ | ------- | -------- | -------- | ------- | ------ |
| 200    | 10      | 25       | 7        | 28      | 0      |
| 200    | 10      | 250      | 35       | 120     | 0      |

## 优化后

| 线程数 | Ramp-up | 循环次数 | 平均延迟 | P99延迟 | 异常率 |
| ------ | ------- | -------- | -------- | ------- | ------ |
| 200    | 10      | 25       | 3        | 6       | 0      |
| 200    | 10      | 250      | 15       | 43      | 0      |