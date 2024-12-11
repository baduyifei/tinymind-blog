---
title: Node.js提供的内置模块
date: 2024-12-11T11:01:43.635Z
---

Node.js提供的内置模块

### 1. 文件系统模块 (fs)
```javascript
const fs = require('fs');

// 读取文件
fs.readFile('test.txt', 'utf8', (err, data) => {
    if (err) throw err;
    console.log(data);
});

// 写入文件
fs.writeFile('test.txt', 'Hello World!', (err) => {
    if (err) throw err;
    console.log('文件已保存');
});
```

### 2. 路径模块 (path)
```javascript
const path = require('path');

// 路径拼接
const fullPath = path.join('/home', 'user', 'docs', 'file.txt');

// 获取文件扩展名
const ext = path.extname('file.txt');  // 返回 '.txt'
```

### 3. HTTP/HTTPS模块
```javascript
const http = require('http');

// 创建HTTP服务器
const server = http.createServer((req, res) => {
    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end('Hello World\n');
});

server.listen(3000);
```

### 4. URL模块
```javascript
const url = require('url');

// 解析URL
const myURL = new URL('https://example.org/foo?bar=1');
console.log(myURL.searchParams.get('bar')); // 1
```

### 5. 事件模块 (events)
```javascript
const EventEmitter = require('events');

class MyEmitter extends EventEmitter {}
const myEmitter = new MyEmitter();

// 监听事件
myEmitter.on('event', () => {
    console.log('触发事件');
});

// 触发事件
myEmitter.emit('event');
```

### 6. 流模块 (stream)
```javascript
const fs = require('fs');

// 创建可读流
const readStream = fs.createReadStream('input.txt');

// 创建可写流
const writeStream = fs.createWriteStream('output.txt');

// 管道传输
readStream.pipe(writeStream);
```

### 7. 加密模块 (crypto)
```javascript
const crypto = require('crypto');

// 创建哈希
const hash = crypto.createHash('sha256');
hash.update('Hello World');
console.log(hash.digest('hex'));
```

### 8. 操作系统模块 (os)
```javascript
const os = require('os');

// 获取CPU信息
console.log(os.cpus());

// 获取内存信息
console.log(os.totalmem());
console.log(os.freemem());
```

### 9. 进程模块 (process)
```javascript
// 获取环境变量
console.log(process.env);

// 获取命令行参数
console.log(process.argv);

// 退出程序
process.exit(0);
```

### 10. 网络模块 (net)
```javascript
const net = require('net');

// 创建TCP服务器
const server = net.createServer((socket) => {
    socket.write('Echo server\r\n');
    socket.pipe(socket);
});

server.listen(1337);
```

### 11. 查询字符串模块 (querystring)
```javascript
const querystring = require('querystring');

// 解析查询字符串
const parsed = querystring.parse('foo=bar&baz=qux');
console.log(parsed); // { foo: 'bar', baz: 'qux' }
```

### 12. 定时器模块
```javascript
// 设置延时
setTimeout(() => {
    console.log('延时执行');
}, 1000);

// 设置间隔
setInterval(() => {
    console.log('定期执行');
}, 1000);
```

### 使用建议

1. **按需引入**
```javascript
// 只引入需要的模块
const { readFile } = require('fs');
```

2. **错误处理**
```javascript
// 使用 try-catch 处理错误
try {
    const data = fs.readFileSync('file.txt');
} catch (err) {
    console.error('读取文件失败:', err);
}
```

3. **异步优先**
```javascript
// 优先使用异步方法
fs.readFile('file.txt', (err, data) => {
    if (err) throw err;
    console.log(data);
});
```

这些模块构成了Node.js的核心功能，让我们能够进行文件操作、网络通信、加密等各种服务器端操作。
