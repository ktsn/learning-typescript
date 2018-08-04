# Program

`Program` is an immutable collection of `SourceFile`s and a `CompilerOptions`. The users can create `Program` by calling `createProgram` (located in `src/compiler/program.ts`) directly or use via language service.

`Program` does not directly communicate with file system. `CompilerHost` is between `Program` and file system.

The users can provide a custom `CompilerHost` to hook some processing. Language service actually customize `CompilerHost` and supports incremental source file parsing for performance. [fork-ts-checker-webpack-plugin](https://github.com/Realytics/fork-ts-checker-webpack-plugin) customizes compiler host to process Vue's SFC (`.vue` file) under the hood.

If the user does not provide compiler host, the default host will be used.

All root files which passed to `createProgram` and referenced files are processed and corresponding source files will be generated during program creation process. `processRootFile` does that and it internally calls `processSourceFile`.
