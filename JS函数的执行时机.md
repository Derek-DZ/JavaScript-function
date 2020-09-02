# JS 函数的执行时机

## 6 个 6

```javascript
let i = 0;
for (i = 0; i < 6; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}
//打印6个6
```

- setTimeout 会在 for 循环执行完，再开始执行
- 在 for 执行完时，i=6
- 此时执行由 for 循环 6 次产生的 6 次 console.log(i)
- 就打印出 6 个 6

## 打印 0,1,2,3,4,5 的方法

- 方法 1

```javascript
for (let i = 0; i < 6; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}
```

- 方法 2
这个方法会有一堆看不懂的警告。但能打印出结果
```javascript
let i = 0;
for (i = 0; i < 6; i++) {
  setTimeout(
    !function (i) {
      console.log(i);
    }(i),
    0
  );
}
```
