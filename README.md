# ts-deps-issue

The repository demonstrates a TypeScript's module resolution problem, under the following conditions:

- Package `c` has a local workspace dependency on packages `a` and `b`.
- Package `b` has a dependency on a released version of package `a`. Generally the package would be taken from NPM, but for simplicity, here we're using a locally packaged version at `./packages/a/a-1.0.0.tgz`.
- Version of local package `a` matches the released version.

With the above setup, if local package `a` has new APIs that are used in package `c`, depending on the order of imports, TypeScript build might fail (see `./packages/c/src/index.ts`).

## Steps to reproduce

1. Clone the repository.
2. Run `pnpm install`.
3. Run `pnpm build`. - Notice that build of package `c` fails.
