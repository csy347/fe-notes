## wesocket



## 安装
``` shell
npm i nodejs-websocket
```

**server.js**

``` js
let ws = require('nodejs-websocket');

let server = ws.createServer((conn) => {
    
});

server.listen(2333, ()=> {
    console.log('server listen 2333');
})
```