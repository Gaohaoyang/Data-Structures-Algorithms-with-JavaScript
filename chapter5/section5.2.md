# 5.2 一个用数组实现的队列

数组中的 `push()` 方法可以在数组末尾加入元素，`shift()` 方法可以在删除数组的第一个元素。

```js
/**
 * 队列的构造函数
 */
function Queue() {
    this.dataStore = [];
    this.enqueue = enqueue; //入队
    this.dequeue = dequeue; //出队
    this.front = front; //读取队首元素
    this.back = back; //读取队尾元素
    this.toString = toString;
    this.isEmpty = isEmpty;
}

/**
 * 入队
 * @param  {[type]} element [description]
 * @return {[type]}         [description]
 */
function enqueue(element) {
    this.dataStore.push(element);
}

/**
 * 出队
 * @return {[type]}         [description]
 */
function dequeue() {
    return this.dataStore.shift();
}

/**
 * 队首元素
 * @return {[type]} [description]
 */
function front() {
    return this.dataStore[0];
}

/**
 * 队尾元素
 * @return {[type]} [description]
 */
function back() {
    return this.dataStore[this.dataStore.length - 1];
}

/**
 * toString
 * @return {[type]} [description]
 */
function toString() {
    var reStr = "";
    for (var i = 0; i < this.dataStore.length; i++) {
        reStr += this.dataStore[i] + '\n';
    }
    return reStr;
}

/**
 * 判断是否为空
 * @return {Boolean} [description]
 */
function isEmpty() {
    if (this.dataStore.length === 0) {
        return true;
    } else {
        return false;
    }
}


///////////////////
//-----test----- //
///////////////////

var q = new Queue();
console.log(q.isEmpty()); //true
q.enqueue('JavaScript');
q.enqueue('HTML');
q.enqueue('CSS');
console.log(q.toString());
console.log(q.dequeue()); //JavaScript
console.log(q.back()); //CSS
console.log(q.front()); //HTML
```
