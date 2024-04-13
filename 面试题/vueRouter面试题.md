# vueRouter面试题

首先我们要安装vue-router，然后进行路由配置，我们可以定义一个routes数组来存储路由规则，路由规则都是一个对象，对象第一个属性是path也就是用户访问的路径，第二个参数是component，这个是用来导入页面对应的组件，第三个参数是name,也就是路由的名称。接下来就是创建路由器，也就是createRouter()，这里首先有路由规则，也就是存储的routes，除了路由规则外，还有history，这里有传统的路由模式和hash模式。vue-router有几个常用的组件，首先router-view它的作用类似于一个占位符，用来显示当前URL组件的内容。也就是我们访问不同的路由时，router-view会自动渲染路由匹配的内容。然后router-link就是类似于普通的<a>标签，点击后跳转页面。

还有Router()方法，比较常见的就是router.push()跳转页面，还有router.back()返回上一个页面。还有Route()，它可以获取当前路径，以及当前路由的参数。然后还有导航守卫，也就是beforeEach,和afterEach，beforeEach就是在路由跳转前触发，这个钩子的作用主要用于登录验证，也就是在路由还没跳转提前告知。afterEach就和beforeEach恰恰相反，它是在路由跳转后触发。这两个函数都接受三个参数，分别为to,from,next。to的作用是将要访问的路径，from代表从哪个路径跳转而来，next是一个函数不带参数的话就是让行的意思，如果带参数的话就是强行跳转。

hash和history区别

hash模式下url中#后面的路径改变不会出现页面加载这是因为#是url描点，代表网页中的某个位置，单单改变#后面的部分，浏览器只会滚到相应的位置。

hash模式兼容性更好

hash值改变不会向后端发送请求，完全属于前端路由

history优点是美观更符合url地址规范