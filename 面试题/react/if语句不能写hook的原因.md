# if语句不能写hook的原因

React的函数组件每次渲染都会有新的状态生成，而且每一次渲染都有一个状态序列，如果在if条件判断里使用，就可能导致在某些情况下的渲染，状态序列丢失，序列就会乱，导致异常。

```js
function MyConputed(){
    const [count, setCount] = useState(0)
    const [name, setName] = useState('lede')
}
```

React状态链表中，序列号：0-->lede

但是如果const [name, setName] = useState('lede')在if条件中执行，就会出现只有0这个状态序列。

**为什么hooks要保证这个状态序列呢？？**

我们使用useState声明状态的时候，只给状态定义了初始值，并没有给状态添加key

以前类的写法

这种写法是对象存储，每个状态都有自己的key和value

```js
state ={
    count: 0,
    name: 'lede'
}
```

函数式组件的写法

这个只有状态，没有key，所以hooks的状态就是使用链表来存储的。哪链表存储的话就是要保持顺序，这样才能每次渲染的序列都对应上。

```js
 	const [count, setCount] = useState(0)
    const [name, setName] = useState('lede')
```

vue3的setup也是函数式组件，为什么就不存在这种问题呢？

Vue3的函数式组件只执行1次：在组件第一次渲染时，就会执行一次setup函数，并创建响应式对象，然后使用闭包进行缓存。后续组件渲染会直接使用缓存渲染函数，不需要重新执行setup函数，所以Vue的状态始终就在一个数据结构里面，顺序不会发生变化。

React的JSX语法本质上是对象，无法使用闭包进行缓存。

而React之所以不使用闭包，是为了实现并发模式（每一次更新的状态都要保存下来，中断后可恢复）。