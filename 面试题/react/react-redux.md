# react-redux

通过createSlice这个库函数，来简化Redux的reducer和action。reducers来定义redux存储的初始状态。reducers对象包含多个函数，每个函数对应一种特定的动作类型。主要负责根据传来的action来更新应用状态。reducer函数接受两个参数当前状态state和动作对象action。可以使用 useDispatch 钩子获取dispatch函数，然后调用dispatch并传入reducers导出的方法来触发reducers里的函数来修改state数据，使用useSelector钩子函数来获取store数据



#### **Redux 的核心概念有哪些？**

- **Store**：存储应用状态的容器。
- **Action**：描述状态变化的普通对象。
- **Reducer**：纯函数，根据 Action 更新状态。
- **Dispatch**：触发 Action 的方法。

#### **Redux 的工作流程是什么？**

1. 用户触发事件（如点击按钮）。
2. 调用 `dispatch(action)`，发送 Action 到 Store。
3. Store 调用 Reducer，传入当前状态和 Action。
4. Reducer 返回新状态，Store 更新状态。
5. 组件通过 `connect` 或 `useSelector` 获取新状态并重新渲染。

