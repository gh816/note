# call，apply,bind区别

首先你得知道call怎么使用其他apple和bind大同小异

```
let dog = {
    name: '旺财',
    sayName(){
        console.log("我是"+this.name);
    },
    eat(food1,food2){
        console.log(this.name+"喜欢吃"+food1+food2);
    }
}

let cat = {
    name: '喵喵'
}
//call是用来改变this指向的，call接收两个参数第一个是this指向，另一个是传的值。如下：
dog.sayName.call(cat) // 我是喵喵
dog.eat.call(cat, "鱼", "肉")// 喵喵喜欢吃鱼肉
//apple方法和call的区别在于传参，apple方法传参使用数组的形式，而call是o用字符串的形式
dog.eat.apply(cat,["鱼","肉"])// 喵喵喜欢吃鱼肉
// bind和call主要区别在于call是直接调用而bind是作为一个返回值返回
let fun =  dog.eat.bind(cat, "鱼", "肉")
fun()// 喵喵喜欢吃鱼肉


```

