---
group:
  title: Redux
  orderNum: 2
---

## Redux 使用方法

> 想要学习 react 必须记住 react 的三大原则，这也是 redux 正常运行的前提。

### 三大原则

1. `单一的数据源`

- 数据管理变的容易只用维护一个 state,受益于单一的 state 时间旅行（撤销和重做也变得容易）

2. `state是只读`

- 确保了视图和网络请求都不能直接修改 state

3. `reducers 是一个纯函数`

- redux 有一个纯函数的概念，即 改变 state 的函数必须是一个纯函数不能带有任何副作用。

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1595869942298&di=9874e3c62d4115777bd359c3fcdcbf71&imgtype=0&src=http%3A%2F%2Fstatic.bookstack.cn%2Fprojects%2Fdvajs%2Fd2d9a3512fd74e48ffdd1a1ead82ccac.png)

- 修改 store 只能通过 dispatch

## 简单 todo 的案例

- 原生 js todoList 案例

```html
<!-- html -->
<div id="todoWrapper">
  <div class="header">
    <input id="input" type="text" placeholder="请输入" />
    <button id="addBtn">添加</button>
  </div>
  <ul class="content">
    暂无数据
  </ul>
</div>
```

预先准备好 js 事件、和渲染添加的函数

```js
// 准备事件 添加 / 删除事件
window.onload = function() {
  // 新增事件
  addBtn.onclick = () => {
    store.dispatch({ type: ADD, payload: { name: input.value } });
  };

  // 删除事件 采用事件委托
  document.addEventListener(
    'click',
    function(e) {
      // console.log(e.target.classList.includes('del'))
      if ([].slice.call(e.target.classList).includes('del')) {
        // 找到是第几个li
        var index = [].indexOf.call(
          e.target.parentNode.parentNode.children,
          e.target.parentNode,
        );
        store.dispatch({ type: DEL, payload: { index } });
      }
    },
    false,
  );
};

// 渲染数据的reder函数
function render() {
  let todoList = store.getState();
  let str = todoList.reduce((htmlStr, a) => {
    return (htmlStr += `<li>${a.name}<button class="del">X</button></li>`);
  }, '');
  document.querySelector('.content').innerHTML = str || '暂无数据';
}
```

redux 第一步（定义 action）

action 是一个普通对象 必须包含 type

```js
// action 是一个普通对象 必须包含type
// 大家都大写，所以就大写了， 其实大小写混用都可以
var ADD = 'ADD';
var DEL = 'DEL';
```

redux 第二步（书写 reducer）

```js
/**
 *previousState  state的值
 action 触发的事件
 */
function reducer(previousState = initialState, action) {
  switch (action.type) {
    case ADD:
      return [...previousState, { ...action.payload }];
    case DEL:
      state.splice(action.payload.index, 1);
      return previousState;
    default:
      return previousState;
  }
}
```

redux 第三步 组装 redux

```js
const { createStore } = Redux;
const store = createStore(reducer);
```

redux 第四步注册数据改变之后的回调

```js
store.subscribe(function() {
  console.log(store.getState());
  render();
});
// 第一次
// 初始化todolist
render();
```

加点功能

1. 数据持久化

```js
    // local session cookie
    const storage = {
        set(key, value) {
            localStorage.setItem(key, JSON.stringify(value))
        },
        get(key) {
            return JSON.parse(localStorage.getItem(key));
        },
        remove(key) {
            localStorage.removeItem(key)
        }
    }
    // 在每次数据发生改变时 存 store
        store.subscribe(function () {
        // 数据做本地缓存
        storage.set('todoList', store.getState());
        // 渲染页面
        render();
    })

    // 更改
      const store = createStore(reducer, storage.get('todoList'));
    })
```

demo 地址

```jsx
// import React from 'react';
// export default function () {
//   return <iframe width='100%' height='500px' src ='https://www.cnblogs.com/sunery/p/10114695.html'/>
// }
```
