## 基本数据类型
### number
toLocalString()
## 数组
### 数组插入
push()
>  插入元素到数组最后

unshift()
> 插入元素到数组开头
### 数组移除
pop()
> 弹出最后一个元素

shift()
> 弹出第一个元素

### 数组的常用api
```javascript
const inventors = [
        { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
        { first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
        { first: 'Galileo', last: 'Galilei', year: 1564, passed: 1642 },
      ]
const people = [
        'Bernhard, Sandra',
        'Bethea, Erin',
        'Becker, Carl',
      ]
const data = [
        'car',
        'car',
        'truck',
      ]
```

forEach((a, index?) => {})

>一般都是对数组中的各项进行各种操作

```javascript
const ans = []
inventors.forEach((inventor) => {
      return ans.push(`${inventor.first} ${inventor.last}`)
  })
```
filter((a) => {return?})

> 一般用作筛选数组中的各项

```javascript
// 匿名函数 @param 数组中的项,此时为inventor
// @return [], 内部项和inventors中的项一般相同,数量一般不同
const ans = inventors.filter(function (inventor) {
      // 匿名函数 @return 一个判断条件
      return inventor.year >= 1500 && inventor.year < 1600
})
// 此时筛选使用16世纪的inventor, 将这些inventor组成数组并返回
```

map((a) => {return?})

> 一般用作对数组中的项修改重构, 当作返回值中的项

```javascript
// 匿名函数 @param 数组中的项,此时为inventor
// @return [], 但是内部项和inventors中的项一般不同,数量一般相同
const ans = inventors.map((inventor) => {
      // 匿名函数 @return 字符串
      return inventor.first + ' ' + inventor.last
})
// 此时将inventor中的first字段和last字段组成字符串, 作为返回数组的项
```

sort((a, b) => {return})
> 对数组中的按照某种排序规则进行排序

```javascript
// 匿名函数 @param1 其中之一的inventor
// 匿名函数 @param2 其中之二的inventor
// @return []
const ans = inventors.sort((inventor1, inventor2) => {
      // 匿名函数 @return 1,0,-1
      return inventor1.year - inventor2.year
})

const ans = people.sort((a, b) => {
      // 解构,预知a.split(', ')返回值为数组,且拥有两项,通过[解构]
      const [aFirst, aLast] = a.split(', ')
      const [bFirst, bLast] = b.split(', ')
	  // 比较第二项,此时第二项为字符串
      return aLast > bLast ? 1 : aLast < bLast ? -1 : 0
      return aLast[0] > bLast[0] ? 1 : aLast[0] < bLast[0] ? -1 : 0
   })
```

reduce((a, b) => {}, 0)

> reduce() 方法对数组中的每个元素按序执行一个由您提供的 reducer 函数，每一次运行 reducer 会将先前元素的计算结果作为参数传入，最后将其结果汇总为单个返回值。
> 如果需要回调函数从数组索引为 0 的元素开始执行，则需要传递初始值。否则，数组索引为 0 的元素将被作为初始值 initialValue，迭代器将从第二个元素开始执行（索引为 1 而不是 0）。

```javascript
// @param1 reducer函数
// @param2 total的初始值,同时可以知道total的类型为 number
// @return 匿名函数 @params1
// 匿名函数 @param1 最终返回的结果, 最后即 ans = total
// 匿名函数 @param2 inventors数组中的每一项
const ans = inventors.reduce((total, inventor) => {
      // @return number,作为下一次迭代的total
      return total + inventor.passed - inventor.year
}, 0)

// @param1 reducer函数
// @param2 obj的初始值,同时可以知道total的类型为对象 {}
// @return 匿名函数 @params1
// 匿名函数 @param1 最终返回的结果, 最后即 ans = obj
// 匿名函数 @param2 data数组中的每一项
const ans = data.reduce((obj, content) => {
      if (!obj[content]) obj[content] = 0
      obj[content]++
      // @return {},作为下一次迭代的obj
      return obj
	}, {})
```

splice(a, b, c?)

> 切割数组, 常用作删除数组元素 和 添加数组元素 spice(x, 0, xxx)
> @param1 开始索引下标
> @param2 从开始索引开始, 切割多少项
> @[param3] 可选参数, ,可为多个, 替换切割部分

slice(a, b?)

> 复制数组
>
> @param1 开始索引下标
>
> @[param2]  结束索引下标,不写则到底

apply()

> aa

```javasciript

```

join()

some()

every()

find()

findIndex()

## 对象

方括号[]

> 访问对象属性,参数为字符串

delete()

> 删除对象中的属性

检查对象是否具有某个属性

> 使用 for...in 语句遍历对象
>
> 使用 Object.keys() 生成由对象的所有属性组成的数组
>
> 使用hasOwnProperty()检验 （最有效）

## 作用域

const 定义常量，但是用const定义的对象或数组内部内容还是可以改变。

Object.freeze(), 锁定对象

任何更改对象的尝试都将被拒绝，如果脚本在严格模式下运行，将抛出错误。

## 闭包

> 保护参数，同时可以使用闭包当工厂，生产函数

```javascript
const a = function(num) {
    let count = num
    return function() {
        console.log(++count)
    }
}

const a1 = a(0)
a1() // 1
a1() // 2
const a2 = a(10)
```

## 事件

### event

> `event.target`指向引起触发事件的元素，而`event.currentTarget`则是事件绑定的元素，只有被点击的那个目标元素的`event.target`才会等于`event.currentTarget`。

## 工具类

### Object.assign(obj1, obj2)

> 对比obj1和obj2，将obj1中obj1和obj2共有的属性改为obj2的属性的值，obj1没有的则添加。
>
> 可用此方法拷贝对象， 可是存在深度不够问题, 引用类型不会深拷贝

```javascript
const aa = Object.assign({name: '123', age:12}, {name:'456', gender: 1})
console.log(aa) // {name:'123', age:12, gender: 1}
// 对象copy
const bb = Object.assign({}, aa)
console.log(bb, aa === bb) // {name:'123', age:12, gender: 1}, false

// 拷贝普通类型深拷贝，引用类型浅拷贝
const a = {
    name: '123',
    email: {
        qq: '@qq.com',
        google: '@google.com'
    },
    say: function() {
        console.log('hi')
    }
}

const b = Object.assign({}, a)
console.log(a.say === b.say) // true
console.log(a.email === b.email) // true
```

### Object.keys(obj).forEach(() => {}) 

> 遍历对象

### JSON.parse(JSON.stringify(obj))

> 可用此方法拷贝对象， 可是存在深度不够问题。（函数无法转换，json不包含函数，可以通过某种方法，不推荐json内包含函数）

```javascript
let person = {name: '123',age: 12}
let person2 = JSON.parse(JSON.stringify(person))
// 对象copy
console.log(person2, person2 === person) // {name: '123', age: 12}, false

// 均为深拷贝，可是无法拷贝function（可能是json没有function格式）
const a = {
    name: '123',
    email: {
        qq: '@qq.com',
        google: '@google.com'
    },
    say: function() {
        console.log('hi')					
    }	
}																	

const b = JSON.parse(JSON.stringify(a))			
/*
    b = {
        name: '123',
        email: {
            qq: '@qq.com',
            google: '@google.com'
        }
}*/
console.log(a.email === b.email) // false
console.log(a.say === b.say) // b.say error
```

## 工具库

lodash

> [Lodash 简介 | Lodash 中文文档 | Lodash 中文网 (lodashjs.com)](https://www.lodashjs.com/)

## ES6

### **reset 操作符** ...

 rest 操作符可以用于创建有一个变量来接受多个参数的函数。 这些参数被储存在一个可以在函数内部读取的数组中。

```javascript
// ...args其实就是数组，可存储不定数个参数
function (...args) {
}
```

### **spread 运算符** ...

作用是将可迭代的(Iterable)对象进行展开。

展开操作符只能够在**函数的参数**中或者**数组**中使用。

```javascript
// 1.数组插入
var fruits = ["apple", "orange", "peach"]
var shoppingList = ["t-shirt", ...fruits, "egg"];

// shoppingList的值：["t-shirt", "apple", "organe", "peach", "egg"]

// 2.函数传参时
function testFunc(x, y, z) {
  console.log(x, y, z);
}

var args = [10, 15, 20];

testFunc(args);  //不正确
testFunc(...args); //正确,将args展开

// 3.实现了Symbol.iterator的对象
var map = new Map();
map.set("a", 1);
map.set("b", 2);
var arr1 = [...map];  //[["a", 1], ["b", 2]]

var set = new Set();
set.add(1);
set.add(2);
set.add(1);
set.add(3);
var arr2 = [...set];  //[1, 2, 3]

function *myGen() {
  yield "hello";
  yield "world";
}
var arr2 = [...myGen()]; //["hello", "world"]
```

### **解构** {  }

#### **解构对象**

```javascript
const user = {name: 'wyz', age: 10,gender: 1}
// 获取对象的值
// ES5
const name = user.name
const age = user.age

// ES6
const { name, age } = user

// 获取对象的值或重命名
const { name: userName, age: userAge } = user

// 解构嵌套对象
const user = {
    name: 'wyz',
    son: {
        name: 'wxz',
        age: 10
    }
}

const { son: { name: sonName, age: sonAge } } = user
```

##### **使用解构赋值将对象作为函数的参数传递**

```javascript
const a = {
    max: 20,
    min: 10
}
// ES5
const add = (a) => a.max + a.min
add(a)

// ES6
const add = ({ max, min }) => max + min
add(a)
```

#### **解构数组**

`扩展运算与数组解构不同，数组的扩展运算会将数组里的所有内容分解成一个由逗号分隔的列表。 所以，你不能选择哪个元素来给变量赋值。`

```javascript
const [a,b,,,c] = [1,2,3,4,5] // a = 1, b = 2, c = 5
```

##### **使用解构赋值配合 rest 操作符来重新分配数组元素**

```javascript
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7]
console.log(arr) // [3,4,5,7] 
```

### **class**

ES6 提供了一个新的创建对象的语法，使用关键字 class。

值得注意的是，`class` 只是一个语法糖，它并不像 Java、Python 或者 Ruby 这一类的语言一样，严格履行了面向对象的开发规范。

```javascript
// 在 ES5 里面，我们通常会定义一个构造函数 constructor，然后使用 new 关键字来实例化一个对象
var A = function(name,age) {
    this.name = name
    this.age = age
    this.gender = 1
}


const b = new A('wyz',20)

console.log(b)

// class 语法只是简单地替换了构造函数 constructor 的写法.
// 注意class关键字声明了一个新的函数,里面添加了一个构造函数.当用 new 创建一个新的对象时,构造函数会被调用。
class A {
    constructor(name, age) {
        this.name = name
        this.age =age
        this.gender = 1
    }
}

const b = new A('wyz',20)
```

### **getter 和 setter**

Getter 函数的作用是可以让对象返回一个私有变量，而不需要直接去访问私有变量。

Setter 函数的作用是可以基于传进的参数来修改对象中私有变量。 这些修改可以是计算，或者是直接替换之前的值。

```javascript

```
### export
#### **用 export 来重用代码块**

```javascript
// 单个export导出多个
const add1 = (x, y) => {
  return x + y
}

const add2 = (x, y) => {
  return x + y + 1
}

export { add1, add2 }

// 多个export
export const add1 = (x, y) => {
  return x + y
}

export const add2 = (x, y) => {
  return x + y + 1
}
```

#### **用 export default 创建一个默认导出**

`export default` 用于为模块或文件声明一个返回值，在每个文件或者模块中应当只默认导出一个值。 此外，你不能将 `export default` 与 `var`、`let` 或 `const` 同时使用。

```javascript
// 第一个是命名函数，第二个是匿名函数。
export default function add(x, y) {
  return x + y;
}

export default function(x, y) {
  return x + y;
}
```


### import
#### **通过 import 复用 JavaScript 代码**

```javascript
import { add1, add2 } from './test.ts'

add1(1,2)
add2(1,2)
```

#### **用 \* 从文件中导入所有内容**

```javascript
import * as mathFunctions from './test.ts'

mathFunctions.add1(1,2)
mathFunctions.add2(1,2)
```

#### **导入一个默认的导出**

这个语法有一处特别的地方， 被导入的 `add` 值没有被花括号（`{}`）所包围。 `add` 只是一个变量的名字，对应 `math_functions.js` 文件的任何默认导出值。 在导入默认导出时，可以使用任何名字

```javascript
import add from "./math_functions.js"
```

### Promise

Promise 是异步编程的一种解决方案 - 它在未来的某时会生成一个值。 任务完成，分执行成功和执行失败两种情况。 `Promise` 是构造器函数，需要通过 `new` 关键字来创建。

```javascript
const myPromise = new Promise((resolve, reject) => {})
```

#### **通过 resolve 和 reject 完成 Promise**

Promise 有三个状态：`pending(等待)`、`fulfilled(完成)` 和 `rejected(拒绝)`。 上一个挑战里创建的 promise 一直阻塞在 `pending` 状态里，因为没有调用 promise 的完成方法。 Promise 提供的 `resolve` 和 `reject` 参数就是用来结束 promise 的。 Promise 成功时调用 `resolve`，promise 执行失败时调用 `reject`， 如下文所述，这些方法需要有一个参数。

```javascript
const myPromise = new Promise((resolve, reject) => {
  // responseFromServer 设置为 true，表示从服务器获得有效响应
  let responseFromServer = true;
  if(responseFromServer) {
    resolve("Promise was fulfilled")
  } else {
    reject("Promise was rejected")
  }
}).then((result) => { // 用 then 处理 Promise 完成的情况,result 即传入 resolve 方法的参数。
  console.log(result)
}).catch((error) => { // 用 catch 处理 Promise 失败的情况,error 即传入 reject 方法的参数。
    console.log(error)
})
```

## console

console.table()

以表格形式输出数据
