# 3.3 使用迭代器访问列表

```js
// 使用迭代器访问列表
// 从前向后遍历
for (list.front(); list.currPos() < list.length(); list.next()) {
    console.log(list.getElement());
}

// 从后向前遍历
for (list.end(); list.currPos() >= 0; list.prev()) {
    console.log(list.getElement());
}
```
