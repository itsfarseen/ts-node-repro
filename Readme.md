# TS Node Repro

## Issue
.d.ts files are ignored when `allowJs && checkJs`
Works fine when either of them are set to false.

## Run

```bash
cd ./myapp-bar
yarn tsc # produces no error
node --loader ts-node/esm main.ts # errors
```

## Error shown

```
(node:700514) ExperimentalWarning: --experimental-loader is an experimental feature. This feature could change at any time
(Use `node --trace-warnings ...` to show where the warning was created)

/home/farseen/Projects/97.Temp/ts-node-types/node_modules/ts-node/src/index.ts:618
    return new TSError(diagnosticText, diagnosticCodes);
           ^
TSError: ⨯ Unable to compile TypeScript:
../myapp-foo/dist/foo.js:1:23 - error TS7031: Binding element 'foo' implicitly has an 'any' type.

1 export function foo({ foo }) {
                        ~~~

    at createTSError (/home/farseen/Projects/97.Temp/ts-node-types/node_modules/ts-node/src/index.ts:618:12)
    at reportTSError (/home/farseen/Projects/97.Temp/ts-node-types/node_modules/ts-node/src/index.ts:622:19)
    at getOutput (/home/farseen/Projects/97.Temp/ts-node-types/node_modules/ts-node/src/index.ts:809:36)
    at Object.compile (/home/farseen/Projects/97.Temp/ts-node-types/node_modules/ts-node/src/index.ts:1111:30)
    at /home/farseen/Projects/97.Temp/ts-node-types/node_modules/ts-node/src/esm.ts:146:38
    at Generator.next (<anonymous>)
    at /home/farseen/Projects/97.Temp/ts-node-types/node_modules/ts-node/dist/esm.js:8:71
    at new Promise (<anonymous>)
    at __awaiter (/home/farseen/Projects/97.Temp/ts-node-types/node_modules/ts-node/dist/esm.js:4:12)
    at transformSource (/home/farseen/Projects/97.Temp/ts-node-types/node_modules/ts-node/dist/esm.js:88:16)

```
