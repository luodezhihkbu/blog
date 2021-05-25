# Vue 修饰符 .sync 的作用

Vue 修饰符 `.scyn` 的作用是，当一个组件的 `props `的值发生改变时，也就是从它的父组件里获取的数据发生改变时，改变的数据也会同步到它的父组件里。

比如下面的代码表示，父组件和子组件的初始数据为100，每当点击一次按钮时，子组件的数据会减去1，这个数据也会同步到父组件中。

```html
<!-- 这是 Father.vue 文件 -->

<template>
  <div class="father">
    父组件数据: {{ fatherNumber }}
    <hr />
    <Child :childNumber.sync="fatherNumber" />
    <!-- 如果不用.sync就要写成下面这样： -->
    <!-- <Child :childNumber="fatherNumber" v-on:update:childNumber="fatherNumber = $event" /> -->
  </div>
</template>

<script>
import Child from "./Child.vue";
export default {
  data() {
    return { fatherNumber: 100 }; 
  },
  components: { Child: Child },
};
</script>

<style>
.father {
  border: 3px solid red;
  padding: 10px;
}
</style>
```

```html
<!-- 这是 Children.vue 文件 -->

<template>
  <div class="child">
    子组件数据: {{childNumber}}
    <button @click="$emit('update:childNumber', childNumber-1)">
      <span>点击减1</span>
    </button>
  </div>
</template>

<script>
export default {
  props: ["childNumber"]
};
</script>

<style>
.child {
  border: 3px solid green;
  padding: 10px;
}
</style>
```

上面的 `:childNumber.sync="fatherNumber"` 其实是`:childNumber="fatherNumber" v-on:update:childNumber="fatherNumber = $event"` 的简写。

当按钮被点击时，`$emit` 会触发事件，将事件记为`update:childNumber`，并将更改后的数据（即 `childNumber-1`）传给 `$event` 。

接着父组件在监听到 `update:childNumber` 后，会将`$event`中的数据同步更新到自己的数据中，即实现了前面说的.scyn的作用。
