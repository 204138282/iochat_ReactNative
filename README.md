ʹ�÷�����
Terminal�У�
1��``$: npm init``		//����package.json����������...��
2��``$: cd ../../iochat``	//cd����������ĿĿ¼
3��``$: node server``		//����node����
4������������Ƽ�.�ȸ���������е�ַ�����롰localhost:3000�� 	//��ʱ�ɿ���Ч��


> **1��package.json�ļ�����  **
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

> 2�������ļ���index.html��server.js��  
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

***����������ǰ�����أ�[https://github.com/204138282/iochat_ReactNative](https://github.com/204138282/iochat_ReactNative)***
```