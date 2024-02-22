---
layout: post
title: "Mixed Content"
author: "qqqqyan"
tags: 前沿
comments: ''
---

# Mixed Cointent

由于http请求不安全，https页面加载http资源报错，有些浏览器禁止并报错，有些则提示仍执行。
## 分类
  1. 被动混合内容（Passive mixed content ）是指不与网页的其余部分交互的内容，因此中间人攻击在拦截或更改该内容后可以执行的操作。被动混合内容是指 images, video, and audio。
  2. 主动混合内容（Active mixed content）与网页整体互动，使攻击者几乎可以对网页执行任何操作。 主动混合内容包括浏览器可下载和执行的 scripts, stylesheets, iframes 和其他。
## 场景
  活动测试时，https的活动页面加载了http的小游戏链接，因此在chrome上无法运行，而在手机中仍可运行。
## 解决
  1. 浏览器的限制，因此需要把资源换成https的，再做旧项目升级：把需要加载的内容升级为https后，对项目中大量http不方便全部修改，因此使用此meta提示浏览器自动以https协议加载数据
  ``` html
  <meta http-equiv="Content-Security-Policy" content="upgrade-insecure-requests" />
  ```
  2. nginx反向代理
