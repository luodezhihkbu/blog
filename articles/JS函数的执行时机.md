# JS 函数的执行时机

每个函数调用的时机不同，最后产生的结果也会不同。

例如下面两段代码。第一段代码，因为 `a=2` 在 `fn()` 前面，`a=2`就会先执行，将2赋值给a，然后调用函数fn，所以输出结果为2。

而第二段代码，因为 `fn()` 在 `a=2` 前面，`fn()`就会先执行，所以输出结果为1。

```javascript
let a = 1
function fn(){
  console.log(a)
}

a = 2
fn()
// 输出为2
```

```javascript
let a = 1
function fn(){
  console.log(a)
}

fn()
a = 2
// 输出为1
```

再比如下面的代码，输出结果为6个6。下面的代码的意思是当i=0时，执行完循环语句后，再执行 `console.log(i)` 打印出i，此时i变成了6。同样，当i=1时，执行完循环语句后，再执行 `console.log(i)` 打印出i，此时i又变成了6。所以最终会打印出6个6。

```javascript
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```

如果想要打印出 0、1、2、3、4、5，把 `let i = 0` 放到for循环里面即可。

```javascript
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```