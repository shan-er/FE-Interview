## ES6+

- [var/let/const区别](#var/let/const区别)


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