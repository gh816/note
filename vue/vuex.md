# vuex

## 创建vuex

![image-20231014210856271](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20231014210856271.png)

![image-20231014210358005](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20231014210358005.png)

用this.$store.state.city是用来获取vuex里的内容的

## actions

![image-20231014211713124](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20231014211713124.png)

changeCity方法接受两个参数第一个参数是上下文ctx，第二个参数组件传出来的数据city

要调用用actions的时候要使用Dispatch方法调用如下：

![image-20231014212054132](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20231014212054132.png)

## mutations

![image-20231014212805551](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20231014212805551.png)

changeCity方法接受两个数据state值的是所有的公用数据，city是commit传来的数据

actions要使用commit方法来调用mutations方法

## 整个流程

首先组件调用actions，actions调用mutations,mutations来改变数据

当组件不是处理批量的数据时可以直接调用mutations方法

![image-20231014215943552](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20231014215943552.png)

## localStorage

