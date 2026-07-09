---
"fhevm-tevm-mocks": minor
---

Split into a standalone repository and drop the deployoor dev dependency from e2e tests (viem deployContract instead). Bump `@zama-fhe/relayer-sdk` to 0.4.4, include CHANGELOG in published files, and tighten the viem peer range to avoid tevm breakage with viem 2.55+ (missing `ekta` chain export).
