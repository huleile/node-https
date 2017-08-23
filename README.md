# node-https

### 签名
  使用 Express 搭建 HTTPS 服务，首先我们要生成签名证书文件，具体请参考：[张丹·粉丝日志--Nodejs创建HTTPS服务器](http://blog.fens.me/nodejs-https-server/), 在此谢过丹哥。

### 创建 Express 项目
  比如我们这里创建 node-https 项目，只需 express -e node-https

### 修改启动文件开启 HTTPS 服务
  我们只需要修改启动文件 bin/www 即可
  在为此文件中添加下面的代码
  ```js
  const https = require('https');
  const path = require('path');
  const fs = require('fs');
  const option = {
    key: fs.readFileSync(`${path.dirname(__dirname)}/privatekey.pem`, 'utf8'),
    cert: fs.readFileSync(`${path.dirname(__dirname)}/hully.crt`, 'utf8')
  };
  const httpsServer = https.createServer(option, app);
  httpsServer.listen(3001);
  ```
  然后启动服务 npm start,在浏览器中输入http://localhost:3000  https://locahost:3001 都可以访问到我们的项目啦
