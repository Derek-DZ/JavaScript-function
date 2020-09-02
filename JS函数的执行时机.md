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
  - 在每次for循环中，JS都创建了一个i并储存当前i的值，相当于有6个i，i的值分别为0,1,2,3,4,5
  - setTimeout会等到for循环结束后执行，打印的结果为0,1,2,3,4,5
  
- 方法 2：使用立即执行函数

```javascript
let i = 0;
for (i = 0; i < 6; i++) {
  !function (i) {
    setTimeout(() => {
      console.log(i), 0;
    });
  }(i);
}
```
