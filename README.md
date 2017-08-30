使用方法：
Terminal中：
1、``$: npm init``		//配置package.json（逐项设置...）
2、``$: cd ../../iochat``	//cd到创建的项目目录
3、``$: node server``		//启动node服务
4、在浏览器（推荐.谷歌浏览器）中地址栏输入“localhost:3000” 	//此时可看到效果


> **1、package.json文件配置  **
```JSX
{
  "name": "iochat",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "start": "node node_modules/react-native/local-cli/cli.js start",
    "test": "jest"
  },
  "dependencies": {
    "react": "16.0.0-alpha.12",
    "react-native": "0.47.2",
    "socket.io": "*",
    "express": "*"
  },
  "devDependencies": {
    "babel-jest": "20.0.3",
    "babel-preset-react-native": "3.0.1",
    "jest": "20.0.4",
    "react-test-renderer": "16.0.0-alpha.12"
  },
  "jest": {
    "preset": "react-native"
  },
  "description": "Simple chat app",
  "main": "server.js",
  "author": "Jeson",
  "license": "ISC"
}
```

> 2、创建文件（index.html和server.js）  
+++++**server.js**
```JSX
var express = require('express');
var app = express();
var server = require('http').createServer(app);
var io = require('socket.io').listen(server);
users = [];
connections = [];

server.listen(process.env.PORT || 3000);
console.log('Server running...');

app.get('/', function (req, res) {
     res.sendFile(__dirname + '/index.html')
});

io.sockets.on('connection', function (socket) {
     connections.push(socket);
     console.log('Connected:%s sockets connected', connections.length);
}

............
```

+++++**index.html**  
```html
<html>

<head>
     <title>IO Chat</title>
     <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
     <script src="http://code.jquery.com/jquery-latest.min.js"></script>
     <script src="/socket.io/socket.io.js"></script>
     <style>
          body {
               margin-top: 30px;
          }

          #messageArea {
               display: none
          }
     </style>
</head>

<body>
</body>

</html>

***其他内容请前往下载：[https://github.com/204138282/iochat_ReactNative](https://github.com/204138282/iochat_ReactNative)***
```