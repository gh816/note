# react路由篇

使用createBrowserRouter函数创建路由，使用RouterProvider函数绑定路由。

![image-20240823203648368](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240823203648368.png)

## react跳转路由方式

1.声明式导航（和vue的router-link类似）

![image-20240823205340957](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240823205340957.png)

2.编程式导航（这个和vue里的useRouter中的router.push相似）

![image-20240823205435449](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240823205435449.png)

## 路由导航传参

1.searchParams

在navigate()用字符串拼接的方法

通过useSearchParams()方法中的get来获取传递的路由参数（这个和vue里的query相似）

![image-20240823211139661](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240823211139661.png)

2.params

在navigate直接拼接值就行

使用useParams()方法来获取传递来的参数

![image-20240823211808612](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240823211808612.png)

上面的id是从初始化路由获取的如下图：

![image-20240823211912016](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240823211912016.png)

## 嵌套路由

![image-20240823223029205](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240823223029205.png)