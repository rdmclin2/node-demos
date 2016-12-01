## Simple App

### 实验目的

1. 学会使用 Node 编写简单的前端应用。

### 操作步骤

（1）新建一个目录

```bash
$ mkdir simple-app-demo
$ cd simple-app-demo
```

（2）在该目录下，新建一个`package.json`文件。

```bash
$ npm init -y
```

`package.json`是项目的配置文件。

（3）安装`jquery`和`webpack`这两个模块。

```bash
$ npm install -S jquery
$ npm install -S webpack
```

打开`package.json`文件，会发现`jquery`和`webpack`都加入了`dependencies`字段，并且带有版本号。

（4）在项目根目录下，新建一个网页文件`index.html`。

```html
<html>
  <body>
    <h1>Hello World</h1>
    <script src="bundle.js"></script>
  </body>
</html>
```

（5）在项目根目录下，新建一个脚本文件`app.js`。

```javascript
const $ = require('jquery');
$('h1').css({ color: 'red'});
```

上面代码中，`require`方法是 Node 特有的模块加载命令。

（6）打开`package.json`，在`scripts`字段里面，添加一行。

```javascript
"scripts": {
  "build": "webpack app.js bundle.js",
  "test": "...."
},
```

（7） 在项目根目录下，执行下面的命令，将脚本打包。

```bash
$ npm run build
```

执行完成，可以发现项目根目录下，新生成了一个文件`bundle.js`。

（8）浏览器打开`index.html`，可以发现`Hello World`变成了红色。

### 练习

1. 修改样式，将标题变为蓝色，然后重新编译生成打包文件。