---
"fhevm-tevm-mocks": patch
---

Fix `state.snapshot()` throwing when destructured off the returned state object. It previously called `this.dumpState()`/`this.loadState()`, the only method relying on `this` instead of closing over the Tevm client directly; calling it as `const { snapshot } = state; await snapshot()` threw `TypeError: Cannot read properties of undefined (reading 'dumpState')`.
