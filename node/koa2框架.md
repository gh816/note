# koa2框架

## ctx含义及作用

ctx及时context缩写表示执行上下文的意思，ctx就是request和response的集合。

ctx.body用来指定服务器响应给客户端的内容，这个就是类似response的内容。

ctx.query是用来获取HTTP请求的querystring(这个是url查询字符部分比如：?100&?200)这个就是request部分