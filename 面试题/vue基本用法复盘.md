# vue基本用法复盘

## axios封装

axios是用来处理http请求的，我们一般会对axios进行封装，因为一个项目里面会很多地方用到axios请求。首先我们需要导入axios，然后用axios.create()来创建axios实例，实例里面是一个对象，对象里面接受一个baseUrl,这个是请求地址的公共部分，还接受timeout，这个是请求超时时间。拿到axios实例之后配置GET请求和POST请求，get请求方法里接受一个请求的地址，param参数。请求成功时候返回then方法，方法里面会有一个response参数这个是请求返回来的参数。失败执行catch方法，返回失败的原因。post请求也接受一个请求的url，还有传输的数据，以及请求头，也就是所传输的数据是以什么类型数据发送的。成功也执行then方法，返回执行成功后的数据。

## promise

promise是用来处理异步请求的。promise有三种状态，pendding(进行中),fulluled(已成功),reject(以失败)，当我们创建一个promise对象时，promise处于pendding状态。而且promise只会从pendding到fulluled或者到reject。promise()接收两个参数，一个是reslove，一个是reject。resolve()表示异步操作成功时的返回结果，reject()表示异步操作失败时的回调函数。promise还有一些常用的方法，then()这个方法可以接受两个参数，一个是异步操作成功的回调函数，另一个是异步操作失败时的回调函数。在then方法还可以return一个新的promise，这才是解决回调地狱的关键。还有catch()这个方法只返回异步操作失败时的回调函数。还有finally()这个方法不管是异步操作成功还是失败有会返回结果。promise还有promise.all()方法这个方法接受数组。数组里面是多个promise对象，只有当所有promise有成功才会返回结果。还有promise.race()这个是用来处理多个异步操作只返回最先执行完的那个结果。allSettled()方法是来处理多个异步操作无论是成功还是失败都会返回结果。

## vueRouter

vueRouter是前端路由，我们使用路由首先要对路由进行配置。首先我们要创建路由器createRouter，路由器里面有路由模式和路由规则，这里的路由规则是一个数组，里面包含对个路由分别对应各个跳转的组件，路由规则里面有url，component路由对应的组件，以及name。配置完路由后还可以配置路由导航。然后vueRouter还有一些组件，比如router-view这个路由组件类似于一个占位符，当进行路由跳转的时候会自动渲染对应路由组件的内容。然后还有router-link这个就类似于a标签点击跳转带指定页面。vueRouter里面还有一些常用的方法比如Router()，可以进行router.push()进行页面跳转。还有router.back()返回上个跳转路由。还有Route()这个方法可以访问到当前路由的路径和路由参数。

## Vuex

vuex是用来存储数据的