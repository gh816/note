# cookies和localStorage和sessionStorage

## 三者的异同

存在时间：

cookie：可以设置失效时间，没有设置的话，默认是关闭浏览器失效

localStorage：除非手动清除，否则永久存在

sessionStorage: 仅在当前网页有效，关闭页面或浏览器就会被清除

存储数据大小：

cookies:4kb左右

localStorage和sessionStorage：可以保存5MB的信息

http请求:

cookies: 每次都会携带在HTTP头中。

localStorage和sessionStorage：仅在浏览器中保存，不参与服务器通信。

应用场景：

cookies常用在用户登录功能上。当用户成功登录后，服务器会向客户端发送一个cookies，这个cookies会在客户端保存下来。通过cookies服务器可以识别用户，并在后续请求中保持用户登录状态。

localStorage和sessionStorage：一般用在客户端缓存数据，比如缓存引用中的静态资源。