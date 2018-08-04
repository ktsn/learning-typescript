# Language Service

- Language Service (LS) is created by `createLanguageService` function defined in `src/services/services.ts`.
- LS will call `synchronizeHostData` before processing something.
  - The function will recreate `Program` to update source files and compiler options.

## create/updateLanguageServiceSourceFile

- These functions are used to create/update source files from LS and DocumentRegistry.
- Looks like all source files created via LS is created/updated by using these functions.
  - They are injected into `Program` as a compiler host.
- They can be replaced to process some non ts files such as `.vue` files. ([Vetur](https://github.com/vuejs/vetur) and [vue-ts-plugin](https://github.com/sandersn/vue-ts-plugin) actually do that)
  - e.g. `ts.createLanguageServiceSourceFile = newCreateLanguageServiceSourceFile`
