# 2.5 迭代器方法

对数组中的每一个元素应用一个函数，可以返回一个值、一组值或新数组。

## 2.5.1 不生成新数组的迭代器方法

* `forEach()` 参数为一个函数，对数组的每一个元素应用该函数。

```js
function square(n) {
    console.log(n, n * n);
}
var nums = [1, 2, 3, 4, 5, 6, 7];
nums.forEach(square);
/*
1 1
2 4
3 9
4 16
5 25
6 36
7 49
*/
```

* `every()` 接受一个返回值为布尔类型的函数，对数组中的每一个元素使用该函数。如果对于多有元素，该函数返回 `true`，则该方法返回 `true`。

```js
function isEven(n) {
    return n % 2 === 0;
}
var nums = [2,4,6,8,10];
console.log(nums.every(isEven)); // true
var nums = [2,4,6,8,1];
console.log(nums.every(isEven)); // false
```

* `some()` 也接受一个返回值为布尔类型的函数，只要有一个元素使得该函数返回 `true`，该方法就返回 `true`。

```js
var nums = [1,3,5,7,9];
console.log(nums.some(isEven)); // false
var nums = [2,3,5,7,9];
console.log(nums.some(isEven)); // true
```

* `reduce()` 参数接受一个函数，返回一个值。该方法会从一个累加值开始，不断对累加值和数组中的后续元素调用该函数，知道数组中的最后一个元素，最后返回得到的累加值。

```js
function add(n1, n2) {
    return n1 + n2;
}
var nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
console.log(nums.reduce(add)); // 55

// 对于字符串数组，可以连接
var strArr = ['I', 'Love', 'Ying', 'ying'];
console.log(strArr.reduce(add)); // ILoveYingying
```

* `reduceRight()` 和 `reduce()` 方法不同的是，它是从右到左执行。

## 2.5.2 生成新数组的迭代器方法

`map()` 和 `filter()`

* `map()` 和 `forEach()` 有点像，却别是 `map()` 返回一个新数组，不改变原数组。

```js
function square(n) {
    return (n, n * n);
}
var nums = [1, 2, 3, 4, 5, 6, 7];
var nums2 = nums.map(square);
console.log(nums); // [1, 2, 3, 4, 5, 6, 7]
console.log(nums2); // [1, 4, 9, 16, 25, 36, 49]
```

* `filter()` 和 `every()` 类似，传入一个返回值为布尔类型的函数。和 every() 不同的是，当对数组中的所有元素应用该函数，结果均为 true 时，该方法并不返回 true，而是返回一个新数组，该数组包含应用该函数后结果为 true 的元素。

    可以用于筛选奇数偶数，筛选成绩是否及格，过滤字符串数组滤掉指定单词。
