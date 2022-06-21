---
title : React纸上谈兵
---
# React纸上谈兵

### 1. Virtual DOM

Virtual DOM 是 一种用JS对象描述DOM对象的方式。修改VirtualDOM的时候，只需要改变原来的DOM对象的属性，以提高重新渲染的性能。

### 2. React框架的主要特点

（待定）

### 3.React生命周期函数

定义：某一个时刻组件自动执行的函数。（生命的进程里总会发生的事情）

例子：

render函数在state或者props改变的时候自动调用。

几个重要的节点：

1. 初始化（Initialization）
2. 挂载（Mounting）
3. 更新（Updation）
4. 去挂载（Unmounting）

挂载阶段：

componentWillMount() {}

render(){} 

componentDidMount() {}

更新阶段：

componentWillReceiveProps() // 父组件render被**重新**（也就是之前已经存在过了）执行，并且**接受**了父组件的参数，子组件的该函数就会被执行。

shouldComponentUpdate() {return bool;}

componentWillUpdate()

render()

componentDidUpdate()

去挂载：

componentWillUnmount()

**什么情况下子组件会被重新渲染呢？**

1.当父组件被重新渲染的时候，子组件也会被重新渲染。

2.render函数在state或者props改变的时候自动调用。

### 4.Redux

![Screen Shot 2021-08-10 at 5.35.17 PM](/Users/xingzhengyang/Desktop/Screen Shot 2021-08-10 at 5.35.17 PM.png)

React Components :  借书的人。

Action Creators： 借书的话。

Store： 管理员。（唯一）

Reducers： 记录本。（必须是**纯函数**）

