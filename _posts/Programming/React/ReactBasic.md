---
categories:React
---

# React 基础

## 为什么使用React

使用原生JavaScript操作Dom繁琐,效率低,每次要重新绘制和排列.

没有组件化,复用率低

## React特点

声明式编码(另一种是命令式)

采用组件化

React Native 可以进行移动端开发

使用**虚拟DOM+Diffing算法**.尽量减少真实DOM的交互

## React 包

react.development.js React核心包

react-dom.development.js 用于支持react操作DOM

babel.min.js 将js转化为jsx

## 虚拟DOM

创建虚拟DOM  
`const VDOM=<h1>Hello React</h1>`

渲染虚拟DOM到页面  
`ReactDom.render(VDOM,document.getElementById('test'))`

虚拟DOM其实就是个Object对象,非常轻便  
最后会被React转化为真实DOM

## JSX

全称JavaScript XML,是JS的扩展语法

## 快速入门

使用 next.js

`npx create-next-app@latest`

