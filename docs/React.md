## React

- [react生命周期函数](#react生命周期函数)
- [为什么虚拟dom会提高性能](#为什么虚拟dom会提高性能)
- [react性能优化方案](#react性能优化方案)
- [项目中有没有使用redux或者是mobx来管理数据](#项目中有没有使用redux或者是mobx来管理数据)

### react生命周期函数
一、初始化阶段：

getDefaultProps:获取实例的默认属性

getInitialState:获取每个实例的初始化状态

componentWillMount：组件即将被装载、渲染到页面上

render:组件在这里生成虚拟的DOM节点

componentDidMount:组件真正在被装载之后

二、运行中状态：

componentWillReceiveProps:组件将要接收到属性的时候调用

shouldComponentUpdate:组件接受到新属性或者新状态的时候（可以返回false，接收数据后不更新，阻止render调用，后面的函数不会被继续执行了）

componentWillUpdate(nextProps,nextState):组件即将更新

render:组件重新描绘

componentDidUpdate:组件更新完成后调用，此时可以获取dom节点。

三、销毁阶段：

componentWillUnmount:组件即将销毁，一些事件监听和定时器需要在此时清除。


### 为什么虚拟dom会提高性能
虚拟dom相当于在js和真实dom中间加了一个缓存，利用dom diff算法避免了没有必要的dom操作，从而提高性能。

具体实现步骤如下：

用 Java 对象结构表示 DOM 树的结构；然后用这个树构建一个真正的 DOM 树，插到文档当中

当状态变更的时候，重新构造一棵新的对象树。然后用新的树和旧的树进行比较，记录两棵树差异

把2所记录的差异应用到步骤1所构建的真正的DOM树上，视图就更新了。


### react性能优化方案
（1）重写shouldComponentUpdate来避免不必要的dom操作。

（2）使用 production 版本的react.js。

（3）使用key来帮助React识别列表中所有子组件的最小变化。


### 项目中有没有使用redux或者是mobx来管理数据
redux ==> action/reducer/store

mobx ==>数据双向绑定