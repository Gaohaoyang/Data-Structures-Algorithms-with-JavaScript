# 使用 Stack 类

有些问题特别适合使用栈去解决，举几个例子。

## 4.3.1 数制间的相互转换

想将数字 n 转换为以 b 为基数的数字，实现转换的算法如下。

算法思路：

1. 最高位为 n%b，将此位压入栈。
2. 使用 n/b 代替 n。
3. 重复步骤 1 和 2，直到 n 等于 0，且没有余数。
4. 持续将栈内元素弹出，直到栈为空，依次将这些元素排列，就得到转换后数字的字符串形式。

> **此算法只针对基数为 2-9 的情况。**

```js
/////////////////////
// 数制间的相互转换 //
/////////////////////

/**
 * 数制间的相互转换
 * @param  {Number} num  数字
 * @param  {Number} base 基数
 * @return {String}      转换后的数字字符串
 */
function mulBase(num, base) {
    var s = new Stack();
    do {
        s.push(num % base);
        num = Math.floor(num /= base);
    } while (num > 0);
    var converted = '';
    while (s.length() > 0) {
        converted += s.pop();
    }
    return converted;
}

///////////////////
//-----test----- //
///////////////////

console.log(mulBase(7, 2)); // 111
```

## 4.3.2 回文

判断一个字符串是否是回文。

使用栈可以轻松完成，将一个字符串依次入栈，完成后，再依次弹出，组成新的字符串，这个字符串刚好是原始字符串的反转。比较两个字符串即可。

```js
///////////////////
//-----回文----- //
///////////////////

function isPalindrome(word) {
    var s = new Stack();
    for (var i = 0; i < word.length; i++) {
        s.push(word[i]);
    }
    var rword = '';
    while (s.length() > 0) {
        rword += s.pop();
    }
    if (rword == word) {
        return true;
    } else {
        return false;
    }
}

///////////////////
//-----test----- //
///////////////////

console.log(isPalindrome('123321')); // true
console.log(isPalindrome('racecar')); // true
console.log(isPalindrome('123')); // false
```

## 4.3.3 递归演示

这里使用栈模拟阶乘。

```js
/**
 * 递归的原始写法
 * @param  {Number} n 数字
 * @return {Number}   结果
 */
function factorial(n) {
    if (n === 0) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}
```

这里使用栈模拟递归，首先将数字5到1压入栈，然后使用一个循环，将数字挨个弹出，得到结果。

```js
/**
 * 栈模拟递归
 * @param  {Number} n 数字
 * @return {Number}   结果
 */
function fact(n) {
    var s = new Stack();
    while (n > 1) {
        s.push(n--);
    }
    var product = 1;
    while (s.length() > 0) {
        product *= s.pop();
    }
    return product;
}

///////////////////
//-----test----- //
///////////////////

console.log(fact(5)); //120
console.log(factorial(5)); //120
```
