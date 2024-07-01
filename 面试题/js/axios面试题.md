# axios面试题

axios是用来处理HTTP请求的，首先我们用axios.create()来创建axios实例，里面接受一个对象，对象里面可以写baseURL，也就是请求地址的公共部分，还有timeout,请求超时时间。拿到axios实例后可以做一些配置，包括请求拦截和响应拦截，axios还有一些常用方法，GET请求和POST请求。Get请求可以接收请求的url地址，还有params参数，成功返回then()，then方法里面有response参数表示服务器返回的参数，失败返回catch方法。post请求接收请求的地址，还有请求的数据，以及请求头，也就是保证发送给服务端的数据的类型。

