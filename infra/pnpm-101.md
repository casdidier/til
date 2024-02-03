https://blog.nrwl.io/setup-a-monorepo-with-pnpm-workspaces-and-speed-it-up-with-nx-bc5d97258a7e

## useful commands:

how to scope commands on single packages using the --filter

```shell
pnpm --filter my-remix-app dev
```

run a command recursively on all the packages in the workspace using the -r flag

```shell
pnpm run -r build
```

can parallelize the run by using --parallel
