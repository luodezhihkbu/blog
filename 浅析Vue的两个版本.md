# 浅析 Vue 的两个版本

Vue 有两个构建版本：完整版和运行时版。分别对应的文件名 vue.js 和 vue.runtime.js 。

完整版是同时包含编译器（compiler）和运行时的版本。编译器是用来将模板字符串编译成为 JavaScript 渲染函数的代码。

运行时版用来创建 Vue 实例、渲染并处理虚拟 DOM 等的代码。基本上就是除去编译器的其它一切。

完整版创建视图是写在 HTML 里或者写在 template 选项里。

```javascript
new Vue({
  template: '<div>{{ hi }}</div>'
})
```

运行时版创建视图是写在 render 函数里，用 h 来创建标签。

```javascript
new Vue({
  render (h) {
    return h('div', this.hi)
  }
})
```

当运行时版配合 vue-loader 使用时，可以直接在 vue 文件里写 HTML 标签，而不写 h 函数。 vue-loader 会把 vue 文件里的 HTML 转化为 h 函数。

```javascript
// App.vue 文件

<template>
  <div id="app">hi</div>
</template>
```

```javascript
// main.js 文件

import App from './App.vue'

new Vue({
  render: h => h(App),
}).$mount('#app')
```