# Node Web

## lesson1

> 创建一个 server.js 文件,首先引入 http 模块

```javascript
// 引入http模块
var http = require("http");
// 创建一个服务
var server = http.createServer();
// 出现错误后触发
server.on("error", function(err) {
  console.log(err);
});
// 端口启用成功后触发
server.on("listening", function() {
  console.log("server启动");
});
// 监听的端口,不设置的话随机分配
server.listen(8080);
// 可以查看服务的端口等信息
console.log(server.address());
```

> 运行 node lesson1.js 启动服务

## lesson2

> 按请求地址返回相应的数据

```javascript
var http = require("http");
var url = require("url"); // 此模块解析url成对象

var server = http.createServer(); // 创建服务
// 服务端请求触发
server.on("request", function(req, res) {
  console.log("有客户端请求了");
  console.log(req.url); // req.url 访问的url
  var urlStr = url.parse(req.url); // url 模块处理url
  switch (urlStr.pathname) {
    case "/":
      // 首页 writeHead 第一个参数设置返回的状态码,返回头的设置
      res.writeHead(200, "success", {
        "content-type": "text/json;charset=utf-8"
      });
      res.end("首页"); // 告诉客户端数据传输完成,这是必需的
      break;
    case "/index":
      // index
      res.writeHead(200, "success", {
        "content-type": "text/json;charset=utf-8"
      });
      res.end("index");
      break;
    case "/home":
      // home
      res.writeHead(200, "success", {
        "content-type": "text/json;charset=utf-8"
      });
      res.end("home");
      break;
  }
});
// 监听端口
server.listen(8000);
```

> 运行 node lesson2.js 启动服务 
1. 分别请求 http://localhost:8000/index
2.         http://localhost:8000/home
3.         http://localhost:8000
          

## lesson3

> 借助fs模块按请求的地址返回对应页面,实现行为的表现分离,创建一个html文件夹,创建名为 index index2 home三个html,内容随意,能区分开三个html即可

```javascript
// 利用fs模块实现表现分离
var http = require("http");
var url = require("url");
var fs = require("fs");

var server = http.createServer(); // 创建服务
var HtmlDir = __dirname + "/html/";
server.on("request", function(req, res) {
  console.log("有客户端请求了");
  // req.url 访问的url
  console.log(req.url);
  var urlStr = url.parse(req.url);
  console.log(urlStr);
  switch (urlStr.pathname) {
    case "/":
      // 首页
      sendHtml(HtmlDir + "index.html", req, res);
      break;
    case "/index":
      // index
      sendHtml(HtmlDir + "index2.html", req, res);
      break;
    case "/home":
      // home
      sendHtml(HtmlDir + "home.html", req, res);
      break;
  }
});
// 返回页面方法
function sendHtml(file, req, res) {
  fs.readFile(file, function(err, data) {
    if (err) {
      res.writeHead(404, {
        "content-type": "text/html;charset=utf-8"
      });
      res.end("这是404页面");
    } else {
      res.writeHead(200, {
        "content-type": "text/html;charset=utf-8"
      });
      res.end(data);
    }
  });
}

server.listen(8000);
```
> 运行 node lesson3.js 启动服务
1. 分别请求 http://localhost:8000/index
2.         http://localhost:8000/home
3.         http://localhost:8000