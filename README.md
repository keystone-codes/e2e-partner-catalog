# e2e-partner-catalog

This repository is a small, real partner catalog for `keystonectl`. It exists so the end-to-end checklist can exercise a second catalog reachable over the network (not `file://`), alongside the default `keystone-codes` catalog, and it doubles as a minimal example of how a partner sets up their own catalog.

## Using this catalog

Add it to `keystonectl` alongside the default catalog:

```bash
keystonectl catalog add https://github.com/keystone-codes/e2e-partner-catalog.git --name partner
```

Once added, packages that exist in more than one catalog (for example `file-mcp`) must be installed with a catalog prefix, such as `partner/file-mcp`, to avoid an ambiguous-package error. Packages unique to this catalog can be installed without a prefix.

## Making your own catalog

This repository follows the catalog format described in [`docs/spec/catalog.md`](https://github.com/keystone-codes/keystonectl/blob/main/docs/spec/catalog.md) in the `keystonectl` repository: a `catalog.yaml` listing packages with a pinned `source` and `ref`, validated by `keystonectl lint`. To package and publish your own service so it can be listed in a catalog like this one, see [`docs/packaging-a-service.md`](https://github.com/keystone-codes/keystonectl/blob/main/docs/packaging-a-service.md).
