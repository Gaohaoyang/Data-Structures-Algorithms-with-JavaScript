# 4.2 栈的实现

使用数组实现栈的底层数据结构。

Stack 类的构造函数。

```js
/**
 * 栈的构造函数
 */
function Stack() {
    this.dataStore = [];
    this.top = 0;
    this.push = push;
    this.pop = pop;
    this.peek = peek;
    this.length = length;
}

/**
 * push 入栈
 * @param  {[type]} element [description]
 * @return {[type]}         [description]
 */
function push(element) {
    this.dataStore[this.top++] = element;
    // 注意++的位置，在top之后，元素先放到当前top的位置，然后top再++
}

/**
 * pop 出栈
 * @param  {[type]} element [description]
 * @return {[type]}         [description]
 */
function pop(element) {
    return this.dataStore[--this.top];
    // 将 top 减小1并赋值给自己（出栈），再将这个值返回
}

/**
 * peek 栈顶元素
 * @param  {[type]} element [description]
 * @return {[type]}         [description]
 */
function peek(element) {
    return this.dataStore[this.top - 1];
    // 返回 top-1 的栈顶元素
}

/**
 * 栈的长度
 * @return {[type]} [description]
 */
function length() {
    return this.top;
    // 返回栈顶的位置，top 是从0开始计算的。
}

/**
 * 清空栈
 * @return {[type]} [description]
 */
function clear() {
    this.top = 0;
    // 将 top 赋值为0，清空一个栈。
}

///////////////////////////////////////////
//-----------------test----------------- //
///////////////////////////////////////////

var s = new Stack();

s.push('dog');
s.push('cat');
s.push('apple');

console.log(s.peek()); // apple
console.log(s.length()); // 3
console.log(s.pop()); // apple
console.log(s.peek()); // cat
```
