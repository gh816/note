# 组件参数效验与非props特性

单要检测父组件传来的值是否是你想要的数据类型可以吧props写成对象的形式**如下面代码所示**

<body>
    <div id="app">
        <child :content="'123'"></child>
    </div>
    <script>
        Vue.component('child', {
            props: {
                content: [String, Number]
            },
            template: '<div>{{content}}</div>'
        })
        let vm = new Vue({
            el: '#app'
        })
    </script>
</body>

![image-20231002150639485](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20231002150639485.png)

props里的validatoe()方法可以限定父组件传来的值的长度

![image-20231002150747456](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20231002150747456.png)

props里的required（）方法要是true说明父组件是必传值的要是false说明不是必传的，假如不传就会使用default里的值