## 三元运算符

```javascript
let x = 20
const answer = x > 10 ? 'is greater' : 'is lesser'
console.log(answer)
```
## 短路求值

```javascript
let val1 = null
const val2 = val1 || 'new'
console.log(val2)
```
## 声明变量

```javascript
let x1, y1, z1 = 3
console.log(x1)
console.log(y1)
console.log(z1)
```
## if 判断

```javascript
let a;
if (!a) {
    // do something...
}
```

## 循环简写

```javascript
function logArrayElements(element, index, array) {
    console.log("a[" + index + "] = " + element);
}
[2, 5, 9].forEach(logArrayElements);
```
## 短路评价 存不存在

```javascript
const dbHost = process.env.DB_HOST || 'localhost';
// 对象属性简写
const obj = {
    x,
    y
};
```
## 箭头函数简写

```javascript
sayHello = name => console.log('Hello', name);

setTimeout(() => console.log('Loaded'), 2000);

list.forEach(item => console.log(item));
```
## 隐式返回值简写

```javascript
function calcCircumference(diameter) {
    return Math.PI * diameter
} // 原

var func = function func() {
    return {
        foo: 1
    };
}; // 原
calcCircumference = diameter => (
    Math.PI * diameter
)

var func = () => ({
    foo: 1
});
```
## 默认参数值

```javascript
function volume(l, w, h) {
    if (w === undefined)
        w = 3;
    if (h === undefined)
        h = 4;
    return l * w * h;
}

volume = (l, w = 3, h = 4) => (l * w * h);

volume(2) //output: 24
```
## 结构赋值

```javascript
const observable = require('mobx/observable');
const action = require('mobx/action');
const runInAction = require('mobx/runInAction');
const store = this.props.store;
const form = this.props.form;
const loading = this.props.loading;
const errors = this.props.errors;
const entity = this.props.entity;

import {
    observable,
    action,
    runInAction
} from 'mobx';
const {
    store,
    form,
    loading,
    errors,
    entity
} = this.props;
```

## 强制参数简写

```javascript
function foo(bar) {
    if (bar === undefined) {
        throw new Error('Missing parameter!');
    }
    return bar;
}

mandatory = () => {
    throw new Error('Missing parameter!');
}

foo = (bar = mandatory()) => {
    return bar;
}
```

## Array.find 简写   find 语法用来查找

```javascript
const pets = [{
        type: 'Dog',
        name: 'Max'
    },
    {
        type: 'Cat',
        name: 'Karl'
    },
    {
        type: 'Dog',
        name: 'Tommy'
    },
]

function findDog(name) {
    for (let i = 0; i < pets.length; ++i) {
        if (pets[i].type === 'Dog' && pets[i].name === name) {
            return pets[i];
        }
    }
}

pet = pets.find(pet => pet.type === 'Dog' && pet.name === 'Tommy');
console.log(pet); // { type: 'Dog', name: 'Tommy' }
```
## 双重飞非位运算简写

```javascript
Math.floor(4.9) === 4 //true

~~4.9 === 4//true]
```