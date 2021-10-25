---
sidebar_position: 4
---


<!-- state-flow -->
<!-- # State Flow -->

1. Create a global state(which is technically a global variable)

2. Subscribe a component(s) to a created global state

3. If a component wants to update a global state, it sends update request

4. When a global state receives update request, it performs the update and send update signal to all components subscribed to it for them to update themselves(re-render)
