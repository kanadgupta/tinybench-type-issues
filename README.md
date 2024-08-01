# `tinybench` type issues

This is a minimal reproduction of [a TypeScript typing issue](https://github.com/tinylibs/tinybench/pull/85) in [`tinybench@2.8.0`](https://www.npmjs.com/package/tinybench/v/2.8.0).

When attempting to import `tinybench` into a CommonJS file that uses a modern TypeScript module setup (i.e., `module: NodeNext`), `tsc` emits the following error when attempting to compile it:

```
index.ts:1:23 - error TS1479: The current file is a CommonJS module whose imports will produce 'require' calls; however, the referenced file is an ECMAScript module and cannot be imported with 'require'. Consider writing a dynamic 'import("tinybench")' call instead.
  To convert this file to an ECMAScript module, change its file extension to '.mts', or add the field `"type": "module"` to '/Users/kanadg/Code/kanadgupta/tinybench-type-issues/package.json'.

1 import { Bench } from "tinybench";
                        ~~~~~~~~~~~


Found 1 error in index.ts:1
```

ATTW also flags these issues: https://arethetypeswrong.github.io/?p=tinybench%402.8.0

## Reproduction Steps

Clone this repository, install the dependencies, and run `tsc`:

```sh
npm install
npx tsc
```
