# 1.3 对象和面向对象编程

使用构造函数定义类。

然后给在添加属性和方法。

实例化时使用 `new` 关键字。

```js
/**
 * 定义一个人的对象
 * @param {String} name 名字
 */
function Person(name) {
    this.name = name; //属性
    this.run = run; //方法
}

function run() {
    console.log('running!');
}

var gao = new Person('gao');

console.log(gao.name); // gao
gao.run(); // running!
```
