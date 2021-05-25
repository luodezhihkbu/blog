# HTML 入门基础

## 一、HTML的发明
HTML在1990年左右诞生，由英国的Tim Berners-Lee（李爵士）发明。

## 二、HTML起手式
HTML起手式就是每次写一个HTML文件时首先要写的代码，这些代码可以理解为HTML的主要结构，之后的代码就已这个结构为基础展开来写。
起手式的写法为输入`!`+`tab`键，接着就会出现如下的代码：
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

## 三、常用的表章节的标签
* `h1`~`h6`：标题，h1代表字体的大小最大，h6最小。
* `section`：章节。
* `article`：文章。
* `p`：段落。
* `header`：页面头部的内容。
* `footer`：页面尾部的内容。
* `main`：主要内容。
* `aside`：旁支内容。
* `div`：划分内容。

## 四、全局属性
全局属性是指所有标签都有的属性。
* `class`：标签的类名。
* `contenteditable`：用户浏览HTML页面时，可以自己在页面上编辑内容。
* `hidden`：隐藏内容。
* `id`：标签唯一具有的名字，但是唯一性没有保证，一般情况下不使用id。
* `style`：更改内容的样式。
* `tabindex`：按tab键时，访问内容按照设置的参数的顺序访问。
* `title`：可以用来显示页面的一行内容显示不完整的内容。

## 五、常用的表内容的标签
* `ol`+`li`：有序列表。
* `ul`+`li`：无需列表。
* `dl`+`dl`+`dd`：描述列表。
* `pre`：保留所有的空格。
* `hr`：分隔符。
* `br`：换行。
* `a`：超链接。
* `em`：强调语气的重要性。
* `strong`：强调内容本身的重要性。
* `code`：用于写代码。
