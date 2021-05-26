# 用 AJAX 实现分页加载

假如有这样一个需求：用户打开页面，看到第一页数据。点击页面的下一页，看到第二页数据。再点击下一页，看到第三页数据。这样一个分页加载的需求用 AJAX 该如何实现呢？

如果对 AJAX 的原理还不太了解，可以参见我之前写的这篇文章[《AJAX 的原理》](AJAX%20的原理.md)，本文将继续按照这篇文章提到的4个步骤来用 AJAX 实现分页加载。

首先，新建 db 文件夹用来存放3个页面的数据。在这个文件夹里，新建要加载的3个页面的 json 数据，数据已提前写好。由于第一页的数据在用户打开页面时就会渲染，所以 page1.json 不需要使用 AJAX 来加载。只需要在 index.html 添加如下的占位符：
```html
<!-- page1.json的占位符 -->
<div id="page">第1页：{{page1}}</div>
```

然后，在 server.js 里的 index.html 路由里添加下面的代码。这样，占位符就会被 page1.json 里的数据所替换。
```javascript
const page1 = fs.readFileSync('db/page1.json').toString();
string = string.replace('{{page1}}', page1);
```

接下来，在 main.js 里创建 AJAX，来加载第二页和第三页的数据，代码如下：
```javascript
let n = 1;
getPAGE.onclick = () => {
  const request = new XMLHttpRequest();
  request.open("GET", `/page${n + 1}.json`);
  request.onreadystatechange = () => {
    if (request.readyState === 4 && request.status === 200) {
      const div = document.createElement("div");
      div.innerHTML = `第${n + 1}页：` + request.response;
      page.appendChild(div);
      n += 1;
    }
    console.log(n);
  };
  request.send();
};
```

最后，在 server.js 里添加 page1.json 和 page2 的路由：
```javascript
else if (path === "/page2.json") {
    response.statusCode = 200;
    response.setHeader("Content-Type", "text/json;charset=utf-8");
    response.write(fs.readFileSync('db/page2.json'));
    response.end();
  } else if (path === "/page3.json") {
    response.statusCode = 200;
    response.setHeader("Content-Type", "text/json;charset=utf-8");
    response.write(fs.readFileSync('db/page3.json'));
    response.end();
```

即实现了前面所述的分页加载需求。


### 【附】源代码链接
https://github.com/luodezhihkbu/ajax-demo