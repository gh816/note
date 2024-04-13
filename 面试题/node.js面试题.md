# node.js面试题

## node.js是什么

1.nodejs是基于Chome V8 引擎的 Javascript 运行时

2.nodejs出现前，js只能在浏览器运行

3.nodejs出现后，js可以在任何安装nodejs的环境运行

## commont.js和ES6 Module 有何区别

1.commontJs是动态引入，执行时引入（可以放在文件任意位置）

2.Module是动态引入，编译时引入（所以module引入要放在文件最顶部）

## node.js 和 前端 js 区别

语法不同：

1.都使用ES语法

2.前端js使用JS Web API

3.nodejs使用node API

![image-20240218205040625](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240218205040625.png)

## nodejs处理 http 面试题

### 如何启动http服务

```
const http = require('http')

const serve = http.createServer((req,res) => {
    console.log('http服务启动');
    //req 可以获取客户端信息
    //res 设置返回信息
    res.end('hello world')
});

serve.listen(3000)
```

### 如何定义路由

```
const http = require('http')

const serve = http.createServer((req,res) => {
    const method = req.method // GET POST 等
    const url = req.url // 获取请求完整 url
    const pathname = url.split('?')[1]
    if(method === 'GET' && pathname === 'username'){
        res.setHeader('Content-Type','text/html; charset=utf-8')
        res.end(`${url}${pathname}`)
    }
});

serve.listen(3000)

```

### 如何返回json格式的数据

```
const http = require('http')

const serve = http.createServer((req,res) => {
    const someObj = {
        name: '张三',
        age: 18
    }
    res.writeHead(200, {'Content-Type': 'application/json'})
    res.end(JSON.stringify(someObj))
})

serve.listen(3000)
```

### session如何实现登录

1.cookie可实现登录校验

2.cookie不能泄露用户信息，所以有了session

3.session存储用户信息，cookie和session关联

![image-20240222145412616](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240222145412616.png)

## nodejs框架面试题

### 框架的作用和价值

1.封装原生的API，让开发更简单

2.规范流程和格式，如1koa2的中间件

3.让开发人员专注于业务和功能的开发

async/await执行顺序的问题

## Mongodb面试题

Schem-数据规范，定义哪些属性	，数据类型，是否必须等

Model-数据模型，提供API操作	Document

Model依赖一个Schema规范，对应一个Collection