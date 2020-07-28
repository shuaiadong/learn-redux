# api

### createStore(reducer, [preloadedState], enhancer) `method`

> reducer(preloadedState, action)`function`

- 接受两个参数, `return` state
- preloadedState
- action 状态发生改变的纯对象
  > preloadedState `any` 初始化的数据
  >
  > enhancer `function` 增强器

`return`

- getState `function` 获取数据的的唯一方法
- dispath `function` 改变数据的唯一方法
- subscribe `function` 数据改变之后的监听函数 `返回一个 卸载监听函数的 function`
