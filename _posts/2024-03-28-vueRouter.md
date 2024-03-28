---
layout: post
title: "vueRouter"
author: "qqqqyan"
tags: 框架
excerpt: vueRouter的主要运作过程...
---

# vueRouter
## 实现目标
1. router管理浏览器、vue应用的关系
2. router挂载到vue中运行

## 关系管理
1. 页面加载，浏览器的url需要被router识别并匹配(match)，然后选择组件进行展示
2. router进行路由转跳时，浏览器的url需要更新(调用HTML5 history API)，且页面组件更新
3. 浏览器进行url更变，router需要识别到并匹配，再更新组件
简言之
1. router推进组件更新
   1. transitionTo & match
   2. defineReactive & <router-view>
2. 推进浏览器url改变
   1. transitionTo & match
   2. history.pushState
3. 捕获浏览器url改变：用户点击浏览器的后退、前进按钮，或者在 js 中调用 HTML5 history API，如 history.back()、history.go()、history.forward()，或者 location.hash = 'xxx'
   1. history.setupListener(onpopstate, onhashchange)

## 挂载
```
init (app: any) {
    process.env.NODE_ENV !== 'production' && assert(
      install.installed,
      `not installed. Make sure to call \`Vue.use(VueRouter)\` ` +
      `before creating root instance.`
    )

    this.apps.push(app)

    if (this.app) {
      return
    }

    this.app = app
}
```