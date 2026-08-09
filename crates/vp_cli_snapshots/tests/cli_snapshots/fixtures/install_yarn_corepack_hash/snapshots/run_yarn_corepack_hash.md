# run_yarn_corepack_hash

## `vpt rm -rf $VP_HOME/package_manager/yarn/4.17.1 $VP_HOME/package_manager/yarn/4.17.1.lock`

Ensure the Corepack-pinned Yarn version is not cached


## `vpt stat-file $VP_HOME/package_manager/yarn/4.17.1 --assert missing`

Yarn 4.17.1 starts uncached

```
<home>/.vite-plus/package_manager/yarn/<version>: missing
```

## `vp run smoke`

A cold vp run accepts the hash and executes the task

```
VITE+ - The Unified Toolchain for the Web

$ vpt print yarn hash accepted ⊘ cache disabled
yarn hash accepted
```

## `vpt stat-file $VP_HOME/package_manager/yarn/4.17.1/yarn/bin/yarn.js --assert file`

vp run finalized the verified Yarn cache

```
<home>/.vite-plus/package_manager/yarn/<version>/yarn/bin/yarn.js: file
```

## `vp run smoke`

A warm vp run reuses the cached Yarn binary

```
VITE+ - The Unified Toolchain for the Web

$ vpt print yarn hash accepted ⊘ cache disabled
yarn hash accepted
```
