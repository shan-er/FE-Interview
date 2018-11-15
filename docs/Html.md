## HTML(5)

- [html5有哪些新特性、移除了那些元素](#html5有哪些新特性、移除了那些元素)
- [如何处理HTML5新标签的浏览器兼容问题](#如何处理HTML5新标签的浏览器兼容问题)
- [对HTML语义化的理解](#对HTML语义化的理解)
- [如何实现浏览器内多个标签页之间的通信](#如何实现浏览器内多个标签页之间的通信)
- [webSocket如何兼容低浏览器](#webSocket如何兼容低浏览器)
- [页面可见性Page Visibility API可以有哪些用途及监听](#页面可见性PageVisibilityAPI可以有哪些用途及监听)

### html5有哪些新特性、移除了那些元素
新特性：
1. 拖拽释放(Drag and drop) API
2. 语义化更好的内容标签（header,nav,footer,aside,article,section）
3. 音频、视频API(audio,video)
4. 画布(Canvas) API
5. 地理(Geolocation) API
6. 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
7. sessionStorage 的数据在浏览器关闭后自动删除
8. 表单控件，calendar、date、time、email、url、search  
9. 新的技术webworker, websocket, Geolocation

移除的元素：
1. 纯表现的元素：basefont，big，center，font, s，strike，tt，u；
2. 对可用性产生负面影响的元素：frame，frameset，noframes；


### 如何处理HTML5新标签的浏览器兼容问题
处理兼容问题有两种方式：
1. IE6/IE7/IE8支持通过document方法产生的标签，利用这一特性让这些浏览器支持HTML5新标签。
2. 使用是html5shim框架

DOCTYPE声明的方式是区分HTML和HTML5标志的一个重要因素，此外，还可以根据新增的结构，功能元素来加以区分

```
<!--[if lt IE 9]>

<script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>

<![endif]-->
```

### 对HTML语义化的理解
1. 用正确的标签做正确的事情；
2. html语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析；
3. 即使在没有样式css情况下也以一种文档格式显示，并且是容易阅读的；
4. 搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO；
5. 使于都源代码的人对网站更容易将网站分块，便于阅读维护理解。

### 如何实现浏览器内多个标签页之间的通信
WebSocket、SharedWorker；

也可以调用localstorge、cookies等本地存储方式；

localstorge另一个浏览上下文里被添加、修改或删除时，它都会触发一个事件，
我们通过监听事件，控制它的值来进行页面信息通信；

注意quirks：Safari 在无痕模式下设置localstorge值时会抛出 QuotaExceededError 的异常；

### webSocket如何兼容低浏览器
1. Adobe Flash Socket 
2. ActiveX HTMLFile (IE) 
3. 基于 multipart 编码发送 XHR 
4. 基于长轮询的 XHR

### 页面可见性PageVisibilityAPI可以有哪些用途及监听
通过 visibilityState 的值检测页面当前是否可见，以及打开网页的时间等;

在页面被切换到其他后台进程的时候，自动暂停音乐或视频的播放；
```
document.addEventListener('visibilitychange', function () {
  // 用户离开了当前页面
  if (document.visibilityState === 'hidden') {
    document.title = '页面不可见';
  }

  // 用户打开或回到页面
  if (document.visibilityState === 'visible') {
    document.title = '页面可见';
  }
});
```