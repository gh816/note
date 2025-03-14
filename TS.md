# TS

## 简单数据类型定义

### Number 数字类型

```
let num1 = 1
let num2 = 2
function add(n1: number, n2: number){
    return n1+n2
}

console.log(add(num1,num2));
```

### 布尔类型

```
let isTrue: Boolean = true

console.log(isTrue);
```

### 字符串类型

```
let firstName: String = "张三"

console.log(firstName);
```

### 数组和元组

```
let list1: number[] = [1,2,3,4]
let list2 = [1,2,3,4]

let list3: any[] = [1,"dss", true]

let person: [number, string] = [1,  "张三"]
```

### 联合类型和字面量类型

```
// 这个就是支持union为数字，字符串，布尔，数组类型
let union : number | string | boolean | string[]
```

```
function merge(n1: number | string, n2: number | string) {
    if(typeof n1 === 'string' || typeof n2 === 'string'){
        return n1.toString() + n2.toString()
    }else{
        return n1 + n2
    }
    
}

console.log(merge(1,2)); // 3 
console.log(merge("张三", 2)); // 张三2
```

字面量类型

```
// 这个代码就是规定union值为0或1或2
let union: 0 | 1 | 2
//和联合类型一起使用
function merge(n1: number | string, n2: number | string, resultType: "as-number" | "as-string") {
    if(resultType === "as-string"){
        return n1.toString() + n2.toString()
    }
    if(typeof n1 === 'string' || typeof n2 === 'string'){
        return n1.toString() + n2.toString()
    }else{
        return n1 + n2
    }
    
}

console.log(merge(1,2,"as-string")); //12
console.log(merge(2,5,"as-number")); // 7
```

### 枚举类型 Enum

```
// 枚举类型真正的类型数据是数字
enum Color {
    red,
    green,
    blue
}

let color = Color.red
console.log(color); // 0
let color2 = Color.green
console.log(color2); // 1

// 指定数据的话后的数据根据指定数据加一前面的数据不变
enum Color {
    red,
    green = 5, 
    blue
}

let color = Color.red
console.log(color); // 0
let color2 = Color.blue
console.log(color2); // 6

// 还可以直接指定数值
enum Color {
	red = 5,
	green = 10,
	blue = 1
}

//还能指定字符串类型
emun Color {
	red = 5,
	green = "green",
	bule = "blue"
}
```

### any 和 unkonwn

any

```
// any可以定义如何数据类型（谨慎使用）
let randomValue: any = 666;
randomValue = true;
randomValue = "acb"
randomValue = {}
randomValue()
randomValue.toUpperCase()

```

unkonwn

```
// unkonwn不保证类型但是保证类型安全
let randomValue: unknown = 666;
randomValue = true;
randomValue = "acb"
randomValue = {}
if(typeof randomValue === 'function'){
    randomValue()
}
if(typeof randomValue === 'string'){
    randomValue.toUpperCase()
}

```

### 类型适配

```
//这个时候message的类型还是any，所以我们要明确告诉ts编译器message真正的类型是string，所以有了类型适配
let messag : any;
message = "abc"

let ddd = (<string>message).endsWith("c")
let ddd2 = (message as string).endsWith("c")
```

## 面向对象

### 对象object

```
const person: any = {
    firstName: "张三",
    lastName: "张",
    age: 18
}

console.log(person.firstName);
```

### Interface

看下面代码没有规定point类型导致完全错乱了当时编译器不会报错

```
let drawPoint = (point) => {
    console.log({x: point.x, y: point.y});
}

drawPoint({x: 105,y: 24})
drawPoint({x: "奥泰斯", y: "aaa"})
drawPoint({wether: '干燥', temperature: "5OC"})
```

下面是用到TS interface

```
let drawPoint = (point: Point) => {
    console.log({x: point.x, y: point.y});
}

drawPoint({x: 105,y: 24})
drawPoint({x: "奥泰斯", y: "aaa"}) //报错
drawPoint({wether: '干燥', temperature: "5OC"}) //报错

interface Point {
    x: number,
    y: number
}
```

### Class类

```
interface IPoint {
    x: number;
    y: number;
    drawPoint: () => void;
    getDistances: (p: IPoint) => number
}

class Point implements IPoint {
    x: number;
    y: number;
    constructor(x: number, y: number) {
        this.x = x;
        this.y = y;
    }
    drawPoint = () => {
        console.log("x: ", this.x, "y: ", this.y);
    }
    getDistances = (p: IPoint) => {
        return Math.pow(p.x-this.x, 2) + Math.pow(p.y - this.y, 2)
    }
}

const point = new Point(2,3)
point.drawPoint
```

## 联合类型和交叉类型

联合类型表示一个值可以是多种类型中的一种，使用 `|` 符号连接多个类型。

交叉类型表示一个值必须同时满足多个类型的条件，使用 `&` 符号连接多个类型。
