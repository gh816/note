# TS面试题

## interface和type区别

1.扩展方式不一样

interface可以通过extends关键字来扩展，实现多个接口的合并。

type使用交叉类型&来实现类似效果

interface扩展

```
interface Animal {
  name: string;
}

interface Dog extends Animal {
  breed: string;
}

let myDog: Dog = {
  name: 'Buddy',
  breed: 'Labrador'
};
```

`type` 的扩展（使用交叉类型）：

```
type Animal = {
  name: string;
};

type Dog = Animal & {
  breed: string;
};

let myDog: Dog = {
  name: 'Buddy',
  breed: 'Labrador'
};
```

2.重复定义

`interface` 的重复定义：

```
interface Person {
  name: string;
}

interface Person {
  age: number;
}

// 合并后的 Person 接口具有 name 和 age 两个属性
let person: Person = {
  name: 'John',
  age: 30
};
```

`type` 的重复定义会导致错误：

```
type Person = {
  name: string;
}

// 以下这行会报错，不能重复定义类型别名
type Person = {
  age: number;
}
```

3.计算属性

- `interface` 不支持定义计算属性。
- `type` 可以使用索引签名来模拟计算属性。

2.枚举（enum）是什么，它的优势，应用案例。枚举和常量枚举的区别

枚举（`enum`）是一种为一组数值赋予有意义名称的方式。

优势：

1. 提高代码的可读性和可维护性：使用有意义的名称代替数值，使代码更易于理解。
2. 类型安全：枚举值具有特定的类型，编译器可以在类型检查时提供更多的保障。

