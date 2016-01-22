# 3.2 实现列表类

```js
function List() {
    this.listSize = 0;
    this.pos = 0;
    this.dataStore = [];
    this.clear = clear;
    this.find = find;
    this.toString = toString;
    this.insert = insert;
    this.append = append;
    this.remove = remove;
    this.front = front;
    this.end = end;
    this.prev = prev;
    this.next = next;
    this.length = length;
    this.currPos = currPos;
    this.getElement = getElement;
    this.contains = contains;
}
```

## 3.2.1 append：给列表添加元素

```js
/**
 * append 在列表末尾添加元素
 * @param  {element} element 要添加的元素
 */
function append(element) {
    this.dataStore[this.listSize++] = element;
}
```

## 3.2.2 find：在列表中查找某一元素

```js
/**
 * find 查找元素
 * @param  {element} element 要查找的元素
 * @return {Number}         查到，返回索引；未查到，返回-1
 */
function find(element) {
    for (var i = 0; i < this.dataStore.length; i++) {
        if (this.dataStore[i] == element) {
            return i;
        }
    }
    return -1;
}
```

## 3.2.3 remove：从列表中删除元素

`remove()` 使用 `find()` 方法返回的位置对数组 dateStore 进行截取。数组改变后，将变量 listSize 的值减 1，以反映列表的最新长度。

```js
/**
 * remove 删除元素
 * @param  {element} element 要删除的元素
 * @return {Boolean}         删除成功，返回 true，不成功返回 false
 */
function remove(element) {
    var foundAt = this.find(element);
    if (foundAt > -1) {
        this.dataStore.splice(foundAt, 1);
        this.listSize--;
        return true;
    }
    return false;
}
```

## 3.2.4 length：列表中有多少个元素

```js
/**
 * length 元素个数
 * @return {Number} 列表长度
 */
function length() {
    return this.listSize;
}
```

## 3.2.5 toString：显示列表中的元素

```js
/**
 * toString
 * @return {Array} 显示当前列表
 */
function toString() {
    return this.dataStore;
}
```

## 3.2.6 insert：向列表中插入一个元素

先找到位置，再使用 `splice()` 操作，同时 `listSize` 加1。

```js
/**
 * insert 插入
 * @param  {element} element 待插入的元素
 * @param  {element} after   在after之后插入元素
 * @return {Boolean}         插入成功，true，不成功false
 */
function insert(element, after) {
    var insertPos = this.find(after);
    if (insertPos > -1) {
        this.dataStore.splice(insertPos + 1, 0, element);
        this.listSize++;
        return true;
    }
    return false;
}
```

## 3.2.7 clear：清空列表中所有的元素

```js
/**
 * clear 清空
 */
function clear() {
    delete this.dataStore;
    this.dataStore = [];
    this.listSize = this.pos = 0;
}
```

## 3.2.8 contains：判断给定值是否在列表中

```js
/**
 * contains 是否包含
 * @param  {element} element 查找的元素
 * @return {Boolean}
 */
function contains(element) {
    for (var i = 0; i < this.dataStore.length; i++) {
        if (this.dataStore[i] == element) {
            return true;
        }
    }
    return false;
}
```

## 3.2.9 遍历列表

```js
/**
 * front
 */
function front() {
    this.pos = 0;
}

/**
 * end
 */
function end() {
    this.pos = this.listSize - 1;
}

function next() {
    if (this.pos < this.listSize) {
        this.pos++;
    }
}

function prev() {
    if (this.pos > -1) {
        this.pos--;
    }
}

function currPos() {
    return this.pos;
}

function moveTo(postion) {
    this.pos = postion;
}

function getElement() {
    return this.dataStore[this.pos];
}
```
