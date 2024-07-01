# MVC和MVVM区别

MVC 通过分离 Model、View和Controller 的方式来组织代码结构。其中View 负责页面的显示逻辑，Model 负责存储页面的业务数据，以及对相应数据的操作。并且 View 和 Model 应用了观察者模式，当 Model 层发生改变的时候它会通知有关 View 层更新页面。Controller 层是 View 层和 Model 层的纽带它主要负责用户与应用的响应操作，当用户与页面产生交互的时候，Controller中的事件触发器就开始工作了，通过调用 Model 层，来完成对 Model 的修改，然后 Model 层再去通知 View 层更新。

MVVM 分为 Model、View、ViewModel:Model 代表数据模型，数据和业务逻辑都在 Model 层中定义;View 代表 UI 视图，负责数据的展示;ViewModel 负责监听 Model 中数据的改变并且控制视图的更新，处理用户交互操作;Model和View 并无直接关联，而是通过 ViewModel 来进行联系的，Model 和ViewModel 之间有着双向数据绑定的联系。因此当 Model 中的数据改变时会触发 View 层的刷新，View 中由于用户交互操作而改变的数据也会在 Model 中同步。这种模式实现了 Model和 View 的数据自动同步，因此开发者只需要专注于数据的维护操作即可，而不需要自己操作DOM。