# js面试题

## 变量类型和计算

### typeof能判断哪些类型

![image-20240114154436644](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240114154436644.png)

### 深拷贝

看懂这个代码就行

```
let result = {
    age: 20,
    name:'xxx',
    address: {
        city: 'beijing'
    },
    arr: ['a','b','c']
}
let result2 = deepClone(result)
result2.address.city = '南昌'
console.log(result.address.city);

function deepClone(obj = {}){
    if(typeof obj !== 'object' || obj == null){
        return obj
    }
    
    let res
    if(obj instanceof Array){
        res = []
    }else{
        res = {}
    }
    for(let key in obj){
        // 保证 key 不是原型的属性
        if(obj.hasOwnProperty(key)){
            // 递归
            res[key] = deepClone(obj[key])
        }
    }
    return res
}
```

### 类型转换

#### 字符串拼接

![image-20240114224529122](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240114224529122.png)

### ==运算符

![image-20240114225125772](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240114225125772.png)

### if语句和逻辑运算

Falsy 值：

- false
- 0
- ''（空字符串）
- null
- undefined
- NaN

Truthy 值：

- 所有非空字符串（包括空格、制表符等）
- 所有数字，包括正数、负数和零
- 所有对象，包括空对象{}
- 所有数组，包括空数组[]

## 原型和原型链

### class

```
class People{
    constructor(name){
        this.name = name
    }
    eat(){
        console.log(`${this.name} eat something`);
    }
}

//子类
class Student extends People{ 
    constructor(name, number){
        super(name)
        this.number = number
    }
    sayHi(){
        console.log(`姓名 ${this.name} 学号 ${this.number}`);
    }
}

const xialuo = new Student('夏洛', 100)
xialuo.sayHi() // 姓名 夏洛 学号 100
console.log(xialuo.name) // 夏洛
console.log(xialuo.number) // 100
xialuo.eat() //夏洛 eat something
console.log(xialuo.__proto__);
console.log(Student.prototype);
```

### 类型判断 - instanceof

作用是判断检查的元素的__proto__能否检查到数据类型的prototype

![image-20240116113909485](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240116113909485.png)

### 原型

原型关系

每个构造函数都有显示原型prototype

原型对象可以放一些属性和方法，共享给实例对象使用

![image-20240116114118810](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240116114118810.png)

原型执行规则

![image-20240116114147862](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240116114147862.png)

原型图

![image-20240116114205029](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240116114205029.png)

### 原型链

![image-20240116114336868](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240116114336868.png)

## 作用域和闭包

### 作用域

![image-20240116151225733](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240116151225733.png)

### 自由变量

![image-20240116152835526](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240116152835526.png)

### 闭包

![image-20240116160433635](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240116160433635.png)

函数作为返回值实例

```
// 函数作为返回值
function create(){
    const a = 100
    return function () {
        console.log(a);
    }
}

const fn = create()
const a = 200
fn() // 100

```

函数作为参数被传递

```
//函数作为参数被传递
function print(fn){
    const a = 200
    fn()
}
const a = 100
function fn() {
    console.log(a)
}
print(fn) // 100
```

上面两个代码总结

闭包：自由变量的查找，是在函数定义的地方，向上级作用域查找不是在执行的地方！！！

闭包造成内存泄漏怎么解决?

内容泄漏是指：函数调用后，函数会自动销毁，但函数中的变量被其他函数访问了，并根据垃圾回收机制，被另一个作用域引用的变量不会被回收，所以会导致内存泄漏。就比如上面第一个例子，fn()执行完后，create函数会自动销毁但函数中的a变量不会被销毁。因为有一个函数访问了变量a。

解决办法：fn = null

### this

![image-20240116210644038](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240116210644038.png)

this的值是在执行的时候确定的不是在定义的时候确定的，注意：箭头函数的this指向永远是上一级

## 单线程和异步

### 异步和同步

![image-20240117142902938](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117142902938.png)

### 异步应用场景

![image-20240117143515011](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117143515011.png)

## JS Web API

### DOM操作

#### DOM本质

DOM 将文档表示为一个节点树，每个节点代表文档中的一个元素、属性、文本或注释。节点之间通过父子关系和兄弟关系连接在一起，形成一个层次结构。开发者可以使用 DOM 提供的方法和属性，遍历节点树、查询和修改节点的属性和内容，以及监听和触发事件。

#### DOM结构操作

新增/插入节点

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .container {
            width: 200px;
            border: 1px solid red;
        }
    </style>
</head>

<body>
    <div id="div1" class="container">
        <p id="p1">一段文字 1</p>
        <p>一段文字 2</p>
        <p>一段文字 3</p>
    </div>
    <div id="div2">
        <img src="https://img1.baidu.com/it/u=2606482731,41621544&fm=253&app=138&size=w931&n=0&f=JPEG&fmt=auto?sec=1705597200&t=3e6036ff386100f13d853a786d4c5114"
            alt="" width="100px" height="100px">
    </div>
    <script src="./dom.js"></script>
</body>

</html>
```



```
const div1 = document.getElementById('div1')
const div2 = document.getElementById('div2')

//新建节点
const newP = document.createElement('p')
newP.innerHTML = 'this is newP'
//插入节点
div1.appendChild(newP)
//移动节点
const p1 = document.getElementById('p1')
div2.appendChild(p1)
```

获取子元素列表，获取父元素

```
const div1 = document.getElementById('div1')
const div2 = document.getElementById('div2')

//新建节点
const newP = document.createElement('p')
newP.innerHTML = 'this is newP'
//插入节点
div1.appendChild(newP)
//移动节点
const p1 = document.getElementById('p1')
div2.appendChild(p1)
// 获取父元素
console.log(p1.parentNode)
// 获取子元素列表
const div1ChildNodes = div1.childNodes
console.log( div1.childNodes )
const div1ChildNodesP = Array.prototype.slice.call(div1.childNodes).filter(child => {
    if(child.nodeType === 1){
        return true
    }else{
        return false
    }
})
console.log(div1ChildNodesP)
```

删除子节点

![image-20240117201147098](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117201147098.png)

#### DOM性能

DOM查询做缓存

![image-20240117201610281](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117201610281.png)

将频繁操作改为一次性操作

```
const list = document.getElementById('list')
// 创建一个文档片段，此时还没有插入到 DOM 结构中
const frag = document.createDocumentFragment()
for(let i = 0;i<10;i++){
    const li = document.createElement('li')
    li.innerHTML = `this is list${i}`
    // 先插入文档片段中
    frag.appendChild(li)
}
// 都完成之后，再统一插入到 DOM 结构中
list.appendChild(frag)
```

#### DOM节点操作

获取DOM节点

![image-20240117204230520](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117204230520.png)

attribute

![image-20240117205547253](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117205547253.png)

property

![image-20240117205235573](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117205235573.png)

property和attribute

![image-20240117205920402](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117205920402.png)

### BOM操作

navigator和screen

![image-20240117211038838](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117211038838.png)

location和history

![image-20240117212720545](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117212720545.png)

### 事件

#### 事件绑定

![image-20240117222318583](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240117222318583.png)

#### 事件冒泡

![image-20240118135036096](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240118135036096.png)

#### 事件代理

 事件代理是一种通过将事件监听器添加到父元素或祖先元素上来管理子元素上的事件的技术，它可以优化事件处理的性能和灵活性。

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style>
    #div3 {
        width: 300px;
        border: 1px solid #0e0606;
        margin: 10px 0;
        padding: 0 10px;
    }
</style>

<body>
    <div id="div3">
        <a href="#">a1</a><br>
        <a href="#">a2</a><br>
        <a href="#">a3</a><br>
        <a href="#">a4</a><br>
        <button>加载更多</button>
    </div>
    <script src="./event.js"></script>
</body>

</html>
```

```
const div3 = document.getElementById('div3')
div3.addEventListener('click', event => {
    event.preventDefault()
    if(event.target.nodeName === 'A'){
        alert(event.target.innerHTML)
    }
})
```

### ajax

#### XMLHttpRequest

```
const xhr = new XMLHttpRequest()
//这个 true意思是异步的请求
xhr.open('GET', './data/text.json', true)
xhr.onreadystatechange = function () {
    if(xhr.readyState == 4){
        if(xhr.status == 200){
            console.log(
                JSON.parse(xhr.responseText)
            )
            alert(xhr.responseText)
        }else{
            console.log('其他情况');
        }
    }
}
xhr.send(null)
```

#### xhr.readyStatus

![image-20240118161944594](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240118161944594.png)

#### xhr.status

![image-20240118162039179](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240118162039179.png)

### 存储

#### cookie

![image-20240121151731520](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240121151731520.png)

缺点

![image-20240121151854030](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240121151854030.png)