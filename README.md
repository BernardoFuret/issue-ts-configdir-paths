# Typescript type check with ${configDir} in paths

Type checking when using `${configDir}` on the `compilerOptions.paths` property
of a reusable root tsconfig extended on a nested package does not work correctly,
as it is unable to find the imports for aliased modules, at the repo root level.

However, type checking in the context of the nested package works correctly.

How to reproduce:

1. Clone the repo
1. Install dependencies: `npm i`
1. Run the type checking script at the repo root level: `npm run type-check`
    * It errors with `TS2307`
1. Run the type checking script at the nested package level: `npm run type-check -w example`
    * Also works if `npm run type-check` directly inside `./w/example`
