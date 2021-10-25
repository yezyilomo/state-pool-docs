---
sidebar_position: 6
---

<!-- state-persistence -->

<!-- # State Persistence -->

Sometimes you might want to save your global states in local storage probably because you might not want to lose them when the application is closed(i.e you want to retain them when the application starts).

**State Pool** makes it very easy to save your global states in local storage, all you need to do is use `persist` configuration to tell **state-pool** to save your global state in local storage when creating your global state.

No need to worry about updating or loading your global states, **state-pool** has already handled that for you so that you can focus on using your states.

`store.setState` accept a third optional parameter which is the configuration object, `persist` is a configuration which is used to tell **state-pool** whether to save your state in local storage or not. i.e

```js
store.setState(key: String, initialState: Any, {persist: Boolean})
```

Since **state-pool** allows you to create global state dynamically, it also allows you to save those newly created states in local storage if you want, that's why both `useGlobalState` and `useGlobalStateReducer` accept `persist` configuration too which just like in `store.setState` it's used to tell **state-pool** whether to save your newly created state in local storage or not. i.e

```js
useGlobalState(key: String, {defaultValue: Any, persist: Boolean})
```

```js
useGlobalStateReducer(reducer: Function, key: String, {defaultValue: Any, persist: Boolean})
```

By default the value of `persist` in all cases is `false`(which means it doesn't save global states to the local storage), so if you want to activate it, set it to be `true`.

What's even better about **state-pool** is that you get the freedom to choose what to save in local storage and what's not to, so you don't need to save the whole store in local storage.

<br/>

### store.LOCAL_STORAGE_UPDATE_DEBOUNCE_TIME

When storing state to local storage, `localStorage.setItem` should not be called too often because it triggers the expensive `JSON.stringify` operation to serialize global state in order to save it to the local storage.

Knowing this **state-pool** comes with `store.LOCAL_STORAGE_UPDATE_DEBOUNCE_TIME` which is the variable used to control debounce time for updating state to the local storage when global state changes. The default value is 1000 ms which is equal to 1 second. You can set your values if you don't want to use the default one.

<br/>
