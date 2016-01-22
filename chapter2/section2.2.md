# 2.2 使用数组

## 2.2.1 创建数组

```js
var arr1 = [];

var arr2 = [1,2,3,4];

var arr3 = new Array();

var arr4 = new Array(1,2,3,4);

var arr5 = new Array(4); // 数组长度
```

判断是否是数组

```js
Array.isArray(arr1);
```

推荐使用 `[]` 创建数组，被认为效率更高。

## 2.2.2 读写数组

使用 `[]` 进行赋值和读取。

## 2.2.3 由字符串生成数组

`split()` 将字符串分割为数组。

## 2.2.4 对数组的整体性操作

* 浅复制

    直接赋值，如下

```js
var nums = [1,2,3];
var samenums = nums;
```


被赋值的数组增加了一个新的引用。当改变原引用的值时，另一个引用也会感知变化。

* 深复制

    将原数组中的每一个元素都赋值一份到新数组中。

```js
/**
 * 深复制
 * @param  {Array} arr1 已知数组
 * @param  {Array} arr2 新数组
 */
function copy(arr1, arr2) {
    for (var i = 0; i < arr1.length; i++) {
        arr2[i] = arr1[i];
    }
}
```
