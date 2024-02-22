---
layout: post
title: "【monorepo】lerna"
author: "qqqqyan"
tags: 工程化
comments: ''
---


# lerna

## 概念
单一仓库管理（monorepo）提供的功能大致有：依赖管理，版本管理，统一执行脚本等

## 使用
1. `lerna init`生成json文件，并配置
```
"useWorkspaces": true,
```
2. 在`package.json`中配置workspace
```
"workspaces": [
  "packages/*"
]
```
3. 在根目录运行`npm i`即可安装所有依赖（旧版本才是bootstrap
4. 在根目录运行`lerna run xxx`即可运行子项目的script
