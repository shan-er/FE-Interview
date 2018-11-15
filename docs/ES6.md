## ES6+

- [var/let/const区别](#var/let/const区别)
- [Promise的理解与使用，手写一个Promise](#手写一个Promise)
- [Promise:以下代码输出什么内容](#Promise:以下代码输出什么内容)
- [jquery的ajax返回的是promise对象吗](#jquery的ajax返回的是promise对象吗)
- [箭头有哪些新特点](#箭头有哪些新特点)


### var/let/const区别

1. var定义的变量，没有块的概念，可以跨块访问, 不能跨函数访问。
2. let定义的变量，只能在块作用域里访问，不能跨块访问，也不能跨函数访问。
3. const用来定义常量，使用时必须初始化(即必须赋值)，只能在块作用域里访问，而且不能修改。

<span style="color: grey">

    关联点： 变量提升、for循环內的setTimeout输出等(es5闭包、es6的let)
    
    看一下以下两个循环输出有何不同：
    for (var index = 0; index < 5; index++) {
        setTimeout(function() {
            console.log(index);
        }, 0);
    }

    for (let index = 0; index < 5; index++) {
        setTimeout(function() {
            console.log(index);
        }, 0);
    }
</span>

### 手写一个Promise
```
let promise = new Promise((resolve, reject) => {
  if (操作成功) {
    resolve(value)
  } else {
    reject(error)
  }
})
promise.then(function (value) {
  // success
}, function (value) {
  // failure
})
```

### Promise:以下代码输出什么内容
```
setTimeout(function () {
  console.log(1)
}, 0);
new Promise(function executor(resolve) {
  console.log(2);
  for (var i = 0; i < 10000; i++) {
    i == 9999 && resolve();
  }
  console.log(3);
}).then(function () {
  console.log(4);
});
console.log(5);

解析：

1.首先先碰到一个 setTimeout，于是会先设置一个定时，在定时结束后将传递这个函数放到任务队列里面，因此开始肯定不会输出 1 。 
2.然后是一个 Promise，里面的函数是直接执行的，因此应该直接输出 2 3 。 
3.然后，Promise 的 then 应当会放到当前 tick 的最后，但是还是在当前 tick 中。 
4.因此，应当先输出 5，然后再输出 4 ， 最后在到下一个 tick，就是 1 。
```
<span style="color: grey">

    关联点： promise.all()、process.nextTick、 promise.then、setTimeout等(事件队列中的宏任务、微任务)
</span>

### jquery的ajax返回的是promise对象吗
jquery的ajax返回的是deferred对象，通过promise的resolve()方法将其转换为promise对象。

var jsPromise = Promise.resolve($.ajax('/whatever.json'));

### 箭头有哪些新特点
1. 不需要function关键字来创建函数
2. 省略return关键字
3. 继承当前上下文的 this 关键字
