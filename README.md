# repro-renovate-package-manager-digest-pinning

## Current behavior

Corepack [recommends](https://github.com/nodejs/corepack/blob/467216281e1719a739d0eeea370b335adfb37b8d/README.md) digest pinning for the package manager version set with the `packageManager` field in `package.json`, but Renovate does not currently support this.

The digest can be manually set by running `corepack use <name[@<version>]>`. For example, running `corepack use pnpm@8.15.6` will set the version to `pnpm@8.15.6+sha256.01c01eeb990e379b31ef19c03e9d06a14afa5250b82e81303f88721c99ff2e6f`.

## Expected behavior

With the config like below, Renovate should pin the `packageManager` version by digest.

```json
{
  "packageRules": [
    {
      "matchDepTypes": ["packageManager"],
      "pinDigests": true
    }
  ]
}
```

Demonstration PR: #1
