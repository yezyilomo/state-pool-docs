---
sidebar_position: 1
---

<!-- getting-started -->

<!-- # Getting Started -->

## Managing Global State

Using **state-pool** to manage global state is very simple, all you need to do is

1. Create a global state by using either `createGlobalState` or `store.setState`(for key based global states)
2. Use your global state in a component through `useGlobalState` or `useGlobalStateReducer` hooks

These two steps summarises pretty much everything you need to use **state-pool**.

Below are few examples showing how to manage global states with **state-pool**.

```js
// Example 1.
import React from "react";
import { store, useGlobalState } from "state-pool";

store.setState("count", 0); // Create "count" global state

function ClicksCounter(props) {
  // Use "count" global state
  const [count, setCount, updateCount] = useGlobalState("count");

  let incrementCount = (e) => {
    setCount(count + 1);
  };

  return (
    <div>
      Count: {count}
      <br />
      <button onClick={incrementCount}>Click</button>
    </div>
  );
}

ReactDOM.render(ClicksCounter, document.querySelector("#root"));
```

```js
// Example 2.
import React from "react";
import { store, useGlobalState } from "state-pool";

store.setState("user", { name: "Yezy", age: 25 });

function UserInfo(props) {
  const [user, setUser, updateUser] = useGlobalState("user");

  let updateName = (e) => {
    updateUser((user) => {
      user.name = e.target.value;
    });
  };

  return (
    <div>
      Name: {user.name}
      <br />
      <input type="text" value={user.name} onChange={updateName} />
    </div>
  );
}

ReactDOM.render(UserInfo, document.querySelector("#root"));
```

<br/>
