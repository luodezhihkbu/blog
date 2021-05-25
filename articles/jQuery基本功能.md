# jQuery 基本功能

## 1、获取元素

```javascript
$(document) //选择整个文档对象

$('#myId') //选择ID为myId的网页元素

$('div.myClass') // 选择class为myClass的div元素

$('input[name=first]') // 选择name属性等于first的input元素
```

## 2、链式操作

链式操作是指选中网页元素以后，可以对它进行一系列操作，并且所有操作可以连接在一起，以链条的形式写出来。比如：
```javascript
$('div').find('h3').eq(2).html('Hello');
``` 
分解开来，就是下面这样：
```javascript
$('div') //找到div元素

.find('h3') //选择其中的h3元素

.eq(2) //选择第3个h3元素

.html('Hello'); //将它的内容改为Hello
``` 

## 3、元素的取值和赋值

jQuery使用同一个函数，来完成取值（getter）和赋值（setter），即"取值器"与"赋值器"合一，也被称为重载。到底是取值还是赋值，由函数的参数决定。
```javascript
$('h1').html(); //html()没有参数，表示取出h1的值

$('h1').html('Hello'); //html()有参数Hello，表示对h1进行赋值
``` 

## 4、元素的移动

jQuery提供两组方法，来操作元素在网页中的位置移动。一组方法是直接移动该元素，另一组方法是移动其他元素，使得目标元素达到我们想要的位置。

假定我们选中了一个div元素，需要把它移动到p元素后面。

第一种方法是使用.insertAfter()，把div元素移动p元素后面：
```javascript
$('div').insertAfter($('p'));
``` 

第二种方法是使用.after()，把p元素加到div元素前面：
```javascript
$('p').after($('div'));
``` 

使用这种模式的操作方法，一共有四对：
```javascript
.insertAfter()和.after()：在现存元素的外部，从后面插入元素

.insertBefore()和.before()：在现存元素的外部，从前面插入元素

.appendTo()和.append()：在现存元素的内部，从后面插入元素

.prependTo()和.prepend()：在现存元素的内部，从前面插入元素
``` 

## 5、元素的操作：复制、删除和创建

复制元素使用`.clone()`。

删除元素使用`.remove()`和`.detach()`。两者的区别在于，前者不保留被删除元素的事件，后者保留，有利于重新插入文档时使用。

清空元素内容（但是不删除该元素）使用`.empty()`。

创建新元素的方法非常简单，只要把新元素直接传入jQuery的构造函数就行了：
```javascript
$('<p>Hello</p>');

$('<li class="new">new list item</li>');

$('ul').append('<li>list item</li>');
``` 

### 参考资料
> [阮一峰：《jQuery设计思想》](http://www.ruanyifeng.com/blog/2011/07/jquery_fundamentals.html)