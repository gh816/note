#  react使用redux

使用react Toolkit创建counterStore,内部属性有一个模块名字，初始化数据，修改数据的同步方法，counterStore中有actions方法，里面有修改数据的方法，还有reducer函数

![image-20240821150634960](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240821150634960.png)

在入口文件store使用tookit使用另一个方法configureStore方法创建根store组合子模块。这个方法接受一个reducer，然后把导出的counterReducer配置给reducer

![image-20240821151755672](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240821151755672.png)

## 为react注入store

通过Provider组件把store参数把创建好的store实例注入到应用中

![image-20240821152344805](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240821152344805.png)

## 在react组件中使用store中的数据

需要使用一个钩子函数-useSelect把store数据映射到组件中

![image-20240821152641058](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240821152641058.png)

## 在react组件中修改store中的数据

修改store数据要使用hook函数-useDispatch，它的作用是生成提交action对象的dispatch函数

![image-20240821155106945](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240821155106945.png)

## 提交action传参实现需求

![image-20240821155936458](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240821155936458.png)