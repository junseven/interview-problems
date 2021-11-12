# 简介
* 是一套用于构建用户界面的渐进式框架。Vue 被设计为可以自底向上逐层应用。
MVVM响应式编程模型，避免直接操作DOM , 降低DOM操作的复杂性。
MVVM：页面输入改变数据，数据改变影响页面数据展示与渲染
M（model）：普通的javascript数据对象
V（view）：前端展示页面
VM（ViewModel）：用于双向绑定数据与页面，对于我们的课程来说，就是vue的实例
渐进式框架，就是用你想用或者能用的功能特性，你不想用的部分功能可以先不用。VUE不强求你一次性接受并使用它的全部功能特性
# VUE核心功能
* 基础功能：页面渲染、表单处理提交、帮我们管理DOM(虚拟DOM)节点
* 组件化开发：增强代码的复用能力，复杂系统代码维护更简单
* 前端路由：更流畅的的用户体验、灵活的在页面切换已渲染组件的显示，不需与后端做多余的交互
* 状态集中管理：MVVM响应式模型基础上实现多组件之间的状态数据同步与管理
* 前端工程化：结合webpack等前端打包工具，管理多种静态资源，代码，测试，发布等，整合前端大型项目。
## vue3
Object.defineProperty 与 Proxy

Object.defineProperty只能劫持对象的属性， 而 Proxy 是直接代理对象

由于Object.defineProperty只能劫持对象属性，需要遍历对象的每一个属性，如果属性值也是对象，就需要递归进行深度遍历。但是 Proxy 直接代理对象， 不需要遍历操作

Object.defineProperty对新增属性需要手动进行Observe

因为Object.defineProperty劫持的是对象的属性，所以新增属性时，需要重新遍历对象， 对其新增属性再次使用Object.defineProperty进行劫持。也就是 Vue2.x 中给数组和对象新增属性时，需要使用$set才能保证新增的属性也是响应式的, $set内部也是通过调用Object.defineProperty去处理的。
