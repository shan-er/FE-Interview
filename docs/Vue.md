## Vue

- [vue生命周期函数](#vue生命周期函数)

### vue生命周期函数
beforeCreate（创建前）：组件刚被创建，组建属性计算之前，如data属性等 执行的钩子函数

created（创建后）：组件刚被创建，组建属性计算之前，如data属性等 执行的钩子函数

beforeMount（载入前）：模板编译、挂载之前执行的钩子函数

mounted（载入后）：编译、挂载后执行的钩子函数

beforeUpdate（更新前）：组件更新之前执行的钩子函数

updated（更新后）：组件更新之后执行的钩子函数

beforeDestroy（销毁前）：当vm.$destroy()被调用 会执行的钩子函数

destroyed（销毁后）：Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。