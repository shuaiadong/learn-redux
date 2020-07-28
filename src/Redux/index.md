---
group:
  title: Redux
  orderNum: 1
---

## Redux 介绍

![redux](https://www.redux.org.cn/assets/images/logo.png)

> redux 是一个状态管理工具, 提供可预测的状态管理。

[docs-中文](https://www.redux.org.cn)

[github](https://github.com/reduxjs/redux/tree/master/src)

### 出现背景

- 随着单页应用开发日益复杂，管理不断变化的 state 非常困难。
- 如果一个 model 的变化会引起另一个 model 变化，那么当 view 变化时，就可能引起对应 model 以及另一个 model 的变化，依次地，可能会引起另一个 view 的变化。
- 直至你搞不清楚到底发生了什么。state 在什么时候，由于什么原因，如何变化已然不受控制。
- 当系统变得错综复杂的时候，想重现问题或者添加新功能就会变得举步维艰。

### redux 的优势

- 数据结构是一个完整的大树，非常容易做到 数据持久化(只需要维护一颗树)。
- 时间旅行 （开发用到的场景比较少见，dev 环境 debug 调试时用的比较多;
- redux 是一个非常小的库。大小仅仅有(只有 2kB，包括依赖)
- 目前大厂推出 react 深度定制框架[dev](https://dvajs.com/)、[umijs](https://umijs.org/zh-CN) 都是基于 redux 状态管理进行深度定制。

### 一些易混淆的概念

想到 redux 通常会想到 react,但是 redux 是独立的 是通过 react-redux 将 react 与 redux 连接起来。`非常多的库都可以与redux一起使用`

接下来的章节让我们一步步揭开 redux 的神秘面纱，了解 redux 的原理。

### [生态-工具包、middleWare](https://www.redux.org.cn/docs/introduction/Ecosystem.html)

### 计划目录

- redux 常用 api 学习
- 手写 redux 代码
- redux 周边插件
  - redux-logger
  - redux-chunk
  - redux-promise
- redux 与 react 结合
- 手写 redux-redux
- saga
