# JS 对象基本用法

## 1. 声明对象

对象（object）是一组“键值对”（key-value）的集合，是一种无序的复合数据集合。

声明对象有两种写法：

```javascript
let obj = {
    'name': 'frank',
    'age': 18
}
```

```javascript
let obj = naw Object ({
    'name': 'frank',
    'age': 18
})
```

## 2. 删除属性

`delete`命令用于删除对象的属性，删除成功后返回`true`。

```javascript
var obj = { p: 1 };
Object.keys(obj) // ["p"]

delete obj.p // true
obj.p // undefined
Object.keys(obj) // []
```

上面代码中，`delete`命令删除对象`obj`的`p`属性。删除后，再读取`p`属性就会返回`undefined`，而且`Object.keys`方法的返回值也不再包括该属性。

## 3. 查看属性

查看自身所有属性：
```javascript
Object.keys(obj)
```
查看自身+共有属性：
```javascript
console.dir(obj)
```
判断一个属性是自身的还是共有的:
```javascript
obj.hasOwnProperty('toString')
```
查看某个属性：
```javascript
obj['key'] // 第一种：中括号语法

obj.key // 第二种：点语法
```

## 4. 增加或修改属性

直接赋值：
```javascript
obj.name = 'frank' 

obj['name'] = 'frank' 
```

批量赋值：
```javascript
Object.assign(obj,{age: 18, gender: 'man'})
```