# 2.6 二维数组和多维数组

JavaScript 只支持一维数组，二维数组使用数组里保存数组的方式实现。

## 2.6.1 创建二维数组

首先创建一个数组，然后让数组的每一个元素也是一个数组。至少要知道多少行，就可以创建一个 n 行 1 列的二维数组了。

```js
var two = [];
var rows = 5;
for (var i = 0; i < rows; i++) {
    two[i] = [];
}
```

可以扩展 JavaScript 数组对象，为其增加一个方法，参数为行数、列数和初始值。

```js
/**
 * 定义二维数组
 * @param  {Number} numrows 行数
 * @param  {Number} numcols 列数
 * @param  {Any}    initial 初始值
 * @return {Array}          二维数组
 */
Array.matrix = function(numrows,numcols,initial) {
    var arr = [];
    for (var i = 0; i < numrows; i++) {
        var columns = [];
        for (var j = 0; j < numcols; j++) {
            columns[j] = initial;
        }
        arr[i] = columns;
    }
    return arr;
};
```

## 2.6.2 处理二维数组的元素

最基本的方式有：按行访问和按列访问。

使用两个for循环处理。

## 2.6.3 参差不齐的数组

数组中每行的元素个数彼此不同。

使用 `.length` 属性可以得到数组长度，所以可以处理的很好。
