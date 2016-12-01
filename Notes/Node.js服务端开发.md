## 主要内容
- Node.js与NPM简介
- Demo1: 基于Node的简单应用
- REST风格的API设计
- Demo2: 设计REST API
- Express介绍
- Demo3: 使用Express 搭建 Web 应用

改编自ruanyf的全栈工程师培训材料的第三讲：Node 应用开发

github地址 : **https://github.com/ruanyf/jstraining**

---

## Node 简介
![42a98226cffc1e17fcdb30594890f603738de976.jpg](resources/FEA37F809864F4FB6C84211CD5F61009.png)

[官网](https://nodejs.org/en/): Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.

主要用途：

- 开发前端应用
- 快速搭建服务
- 架设网站

---

## npm

安装 Node 的时候，会同时安装 npm。

```bash
$ npm -v
```

它是 Node 的模块管理器，开发 Node 项目的必备工具，类似于Java的Maven,
如果觉得使用npm下载模块的时候速度缓慢，可以设置npm的源为淘宝源:
```
$ npm config set registry https://registry.npm.taobao.org
```

---

## 课堂练习：Node 的简单应用
自己动手在 Node 里面，编写并编译一个前端脚本。
[Demo1 : Simple App](quiver:///notes/FC145621-4024-448C-A043-D242E3FE9A59)

---

## Node 开发前端脚本的好处

1. 模块机制
1. 版本管理
1. 对外发布
1. 持续集成的标准开发流程

---

## REST API

REST 是浏览器与服务器通信方式的一种设计风格。

它的全称是“REpresentational State Transfer”，中文意为”表现层状态转换“。

- Resource：资源
- Representation：表现层
- State：状态
- Transfer：转换

---

## REST 的核心概念
REST是”REpresentational State Transfer”，一种翻译是”表现层状态转移”

1. 互联网上所有可以访问的内容，都是资源。
1. 服务器保存资源，客户端请求资源。
1. 同一个资源，有多种表现形式。
1. 协议本身不带有状态，通信时客户端必须通过参数，表示请求不同状态的资源。
1. 状态转换通过HTTP动词表示。

简单来说，REST是所有web应用都应该遵守的架构设计指导原则，每一个URL代表一种资源，客户端通过四个HTTP动词，对服务器端资源进行操作，实现”表现层状态转化”。

---

## URL 设计

URL 是资源的唯一识别符。

- /store/1
- /store/2
- /store/1/employee/2

---

## 查询字符串
查询字符串表示对所请求资源的约束条件。如果记录数量很多，服务器不可能都将它们返回给用户。API应该提供参数，过滤返回结果。
```
?limit=10：指定返回记录的数量
?offset=10：指定返回记录的开始位置。
?page=2&per_page=100：指定第几页，以及每页的记录数。
?sortby=name&order=asc：指定返回结果按照哪个属性排序，以及排序顺序。
?animal_type_id=1：指定筛选条件
```

---

## HTTP 动词

|操作|SQL方法|HTTP动词|
|----|-------|--------|
|CREATE|INSERT|POST|
|READ|SELECT|GET|
|UPDATE|UPDATE|PUT/PATCH|
|DELETE|DELETE|DELETE|

```
GET /v1/stores/1234 若要检索某个资源，应该使用 GET 方法。
PUT /v1/stores/1234 若要更改资源状态或对其进行更新，应该使用 PUT 方法。
POST /v1/stores 若要在服务器上创建资源，应该使用 POST 方法。
DELETE /v1/stores/1234 若要删除某个资源，应该使用 DELETE 方法。
```

---

## 课堂练习：REST API
[Demo2: Rest Api](quiver:///notes/12CAD3E3-3BD7-4C5D-B039-AA84BFFCBB7F)

- 延伸阅读: [Restful API浅析 之设计原则与案例修正](http://mclspace.com/2015/11/03/restful-note/)

---

## Express

Express 是最常用的 Node 框架，用来搭建 Web 应用，类似于Java里的Spring以及Ruby里的ROR。

![express.png](resources/F406DB5658B5D0DADE4D70A989560439.png)

---

## 课堂练习：Express 搭建 Web 应用

[Demo3: Express搭建Web应用](quiver:///notes/C7CE3709-C792-4968-A455-5EFB0DE6210F)

---

定义一个 Web 应用实例，并且启动它。

```javascript
var express    = require('express');
var app        = express();

var port = process.env.PORT || 8080;

app.listen(port);
console.log('Magic happens on port ' + port);
```

---

定义一个路由

```javascript
var router = express.Router();

router.get('/', function(req, res) {
  res.send('<h1>Hello World</h1>');
});

app.use('/home', router);
```

---

中间件：对 HTTP 请求进行加工。

```javascript
router.use(function(req, res, next) {
  console.log('There is a requesting.');
  next();
});
```