# vue面试题

## vue2和vue3的区别

1.生命周期
对于生命周期，整体上变化不大，vue3大部分生命周期在vue2上加上on，功能上类似，不过要注意的是Vue3是组合式API使用生命周期时需要引入，
而Vue2是选项式API可以直接调用生命周期函数。vue2有8种生命周期函数而vue3只有6种。vue3里setup是围绕beforeCreate和Created生命周期
勾子运行的，所以不需要去定义。
2.多根节点
在vue3是支持多个根节点的，比如一个tempate中可以包含tempate
3.vue2使用的是选项式API而Vue3使用的是组合式API。选项式API基于选项对象的组件编写方式（例如data,methods,computed,watch），组合式API是基于函数的组件编写方式(例如setup，reactive,computed,watch)，

4.v-if和v-for的优先级

在vue2中v-for的优先级高于v-if，可以放在一起使用，但不建议

在vue3中v-if的优先级高于v-for，一起使用会报错。可以在外部加一个标签将v-for移到外层

5.diff算法不同

vue2中的diff算法

遍历每一个虚拟节点，进行虚拟节点比对，并返回一个patch对象，用来存储两个节点不同的地方。

缺点：比较每一个节点，而对一些不参与更新的元素，进行比较有点消耗性能

vue3的diff算法

在初始化的时候会给每一个虚拟节点添加patchFlags。只会比较patchFlags发生变化的节点，进行更新。而对patchFlags没有变化的元素直接复用。

6.响应式原理不同



vue2通过Object.defineProperty()的get()和set()来做数据劫持，结合发布者订阅者模式来实现。

vue3通过proxy代理方式实现

Object.defineProperty无法监听到数组方法，Object.defineProperty只能劫持对象属性，从而需要对每个对象，每个属性进行变遍历，如果，属性值是对象，还需要深度遍历。

proxy的优势：不仅可以代理对象，还可以代理数组。还可以代理动态增加的属性。

7.vue3打包速度更快不再打包没用到的模块。

Vue 3 的模块被设计为更易于 tree-shaking，这意味着构建时可以更轻松地剔除项目中未使用的代码，减小最终打包文件的体积。

## v-if和v-show

v-if在渲染的时候,如果条件为假，什么也不操作，也不会生成dom。当条件为真的时候，开始生产dom，当条件为假的时候卸载dom。

v-show不管条件是真还是假，第一次渲染的时候都会编译出来，也就是标签都会添加到DOM中。之后切换的话，通过display：none；样式来隐藏元素。可以说是只改变css的样式。

选择上如果更新不频繁就用v-if，如果更新频繁就用v-show

## 解释一下对Vue生命周期的理解

### 是什么vue的生命周期

就是一个实例从创建到销毁的过程

### 生命周期的作用是什么

当程序运行到某个阶段会触发相应的生命周期钩子，可以让我们在生命周期的特定阶段进行相关的业务代码编写

### vue生命周期有哪几个阶段

1.beforeCreate：创建前，在当前阶段的data,methods,computed,watch上的数据都不会被访问

2.created:创建后，此时可以使用数据，更改数据，但此处无法与DOM进行交互。

3.berforeMount:挂载前，此时虚拟DOM已经创建完成，即将开始渲染。

4.mounted：挂载后，真实的DOM挂载完毕，数据完成双向绑定，可以访问DOM节点。

5.beforeUpdate：更新前，虚拟DOM重新渲染前触发，可以在当前阶段更改数据。不会造成重渲染。

6.updated:更新后，当前DOM完成更新。

7.beforeDestroy:实例销毁前当前阶段实例可以正常使用

8.destroyed:实例销毁后，这个时候只剩下DOM空壳。

### 第一次页面加载会触发那几个钩子

beforeCreate，created，berforeMount，mounted

### DOM渲染在哪个周期就已经完成

mounted

### 多组件（父子组件）中生命周期调用顺序

组件调用顺序是先父后子，渲染完成顺序是先子后父。组件销毁操作是先父后子，销毁完成的顺序是先子后父。

## Vue2实现双向数据绑定原理是什么？

数据劫持结合发送者-订阅者模式的方式来实现的，通过Object.defineProperty来劫持各个属性的setter,getter,在数据变动时发布消息给订阅者，触发相应的监听回调。

### object.defindProperty缺点

1.深度监听，需要递归到底，一次性计算量大

2.无法监听新增属性/删除属性

3.无法原生监听数组，需要特殊处理

## vue3响应式数据原理是什么？

vue3响应式原理是利用proxy对数据代理。通过reactive()函数给每一个对象都包一层proxy，通过proxy监听属性的变化，从而实现对数据的监控

## 为何在v-for中用key

必须使用key,且不能是index和random

diff算法中通过tag和key来判断，是否是sameNode

减少渲染次数，提升渲染性能

## Vue组件如何通讯（常见)

父组件通过v-bind在组件上绑定属性，然后子组件通过props接收并使用传过来的数据，在vue3中用defineProps函数代替props

子组件向父组件传值通过this.$emit()这个方法传两个参数一个是事件名另一个是传的值，父组件就用@传过来的事件名来绑定参数

vuex

## 为何组件data必须是一个函数?

目的是为了防止多个组件实例对象之间共用一个data，产生数据污染

## 如何将组件所有props传递给子组件？

## 何时使用异步组件

在vue3中可以使用defindAsyncComponent函数来定义异步组件，通过按需加载

## 何时使用keep-alive

## computed和watch区别

1.computed是计算属性，计算的属性值发生变化，数据才会更新。watch是监听属性变化，执行相应操作。

2.computed有缓存，当依赖的属性没有发生变化，则取缓存中的数据。watch监听值发生变化都会调用回调函数。