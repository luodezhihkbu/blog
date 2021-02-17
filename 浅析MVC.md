# 浅析 MVC

## 1. MVC 的三个对象

MVC 分别表示 Model，View，Controller 三个对象。

### 1.1 Model

Model 指数据模型，通过创建一个 m 对象来操作所有的数据。

对数据进行更删改查的伪代码示例：

```javascript
const m = {
    create() {},
    delete() {},
    update() {},
    get() {}
}
```

### 1.2 View

View 指视图，通过创建一个 v 对象负责所有的UI界面。

对页面进行初始化和渲染的伪代码示例：

```javascript
const v = {
    el: null,
    html: `<div></div>`,
    init() {},
    render() {}
}
```

### 1.3 Controller

Controller 指控制器，通过创建一个 c 对象负责除 Model 和 View 以外的操作。

点击事件的伪代码示例：

```javascript
const c = {
    init() {},
    events: {
        'click #id': 'id',
    },
    id() {},
    autoBindEvents() {}
}
```

## 2. EventBus

EventBus 用于对象之间的通信。常用的 API 有 trigger 和 on 。trigger 用于触发事件， on 用于监听事件。

使用 eventBus 时，m 和 v 互相不知道对方的细节，但是却可以调用对方的功能。

比如下面的代码表示，当 m 中的 update 被调用时， v 中的 eventBus.on 会监听到 eventBus.trigger 传过来的参数 m:updated ，从而调用 render() 。

```javascript
const eventBus = $(window) // 需要先声明eventBus

const m = {
    update() {
        eventBus.trigger('m:updated')
    },
}
const v = {
    eventBus.on('m:updated', () => {
        render()
    })
}
```

## 3. 表驱动编程

当出现大批类似但不重复的代码，看看哪些才是重要的数据，把重要的数据做成哈希表，从而简化代码，这就叫做表驱动编程。

## 4. 模块化



