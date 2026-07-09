# Changesets

This repo uses [Changesets](https://github.com/changesets/changesets) for versioning and publishing.

When you make a change that should trigger a release, run `pnpm changeset` and describe the change. On merge to `main`, the release workflow opens a "Version Packages" PR; merging that PR publishes to npm via OIDC trusted publishing.
