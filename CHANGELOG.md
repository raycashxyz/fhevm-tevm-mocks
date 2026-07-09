# fhevm-tevm-mocks

## 0.4.1

### Patch Changes

- b908b0f: Fix `state.snapshot()` throwing when destructured off the returned state object. It previously called `this.dumpState()`/`this.loadState()`, the only method relying on `this` instead of closing over the Tevm client directly; calling it as `const { snapshot } = state; await snapshot()` threw `TypeError: Cannot read properties of undefined (reading 'dumpState')`.

## 0.4.0

### Minor Changes

- 98222eb: Split into a standalone repository and drop the deployoor dev dependency from e2e tests (viem deployContract instead). Bump `@zama-fhe/relayer-sdk` to 0.4.4, include CHANGELOG in published files, and tighten the viem peer range to avoid tevm breakage with viem 2.55+ (missing `ekta` chain export).

## 0.3.0

### Minor Changes

- 7913ff9: Point repository metadata at `raycashxyz/deployoor` after transferring the GitHub org.

## 0.2.0

### Minor Changes

- ff9c849: Add `fhevm-tevm-mocks`: Tevm-native adapter primitives for running Zama FHEVM mock tests in an in-memory EVM. You own the Tevm instance and pass it in; `createFhevmTevmRuntime(tevm)` installs the Zama host contracts, initializes ACL/KMSVerifier/InputVerifier storage, wires the mock relayer RPC handlers, and returns viem wallet/public clients plus a `MockFhevmInstance` for SDK-style encryption and decryption. `tevm` and `viem` are peer dependencies. The package is deploy-framework-agnostic — deploy your contracts with viem, Hardhat, Foundry, or any tool.

### Patch Changes

- 4e505d0: Compat hardening from packaging/resolution audit: `sideEffects: false` on all publishable packages; `typesVersions` on `deployoor/plugin` and `deployoor/generate` for legacy `moduleResolution: "node"`; Node `>=20` engines on tevm-dependent packages; align tevm as a hard dependency and declare `viem >=2.49` where tevm requires it; document TypeScript-first codegen and CJS/ESM caveats; add a Windows CI smoke job.
