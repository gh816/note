# GET请求和POST请求区别

Post 和GET是HTTP请求的两种方法：

区别：

1.GET请求用于获取数据，一般不会对服务器资源产生影响。而post请求一般是对服务器发送请求数据，会对服务器资源产生影响。

2.浏览器GET请求缓存，很少对post请求缓存。

3.GET请求通过查询字符串传参，post通过请求体传参。

4.GET请求可以将请求参数放入url向服务器发送，相对post请求来说不安全，因为请求的url会保留在历史记录中。