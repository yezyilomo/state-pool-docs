---
sidebar_position: 3
---

<!-- managing-local-state -->

<!-- # Managing Local State -->

**state-pool** allows you to manage local states too, it is shipped with `useLocalState` hook which is equivalent to `useState` with improved way to update state(especially nested ones).

Below are few examples showing how to manage local states with **state-pool**.

```js
// Example 1.
import React from "react";
import { useLocalState } from "state-pool";

function ClicksCounter(props) {
  const [count, setCount, updateCount] = useLocalState(0);

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

<br/>

```js
// Example 2.
import React from "react";
import { useLocalState } from "state-pool";

function UserInfo(props) {
  const [user, setUser, updateUser] = useLocalState({ name: "Yezy", age: 25 });

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
