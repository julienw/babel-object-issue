1. Clone the project
2. Run `npm i`
3. Run `npx babel-node Object.js`

The error we get is:
```
Object.defineProperty(exports, "__esModule", {
    ^

    ReferenceError: Cannot access 'Object' before initialization
    at Object.<anonymous> (/home/julien/travail/git/babel-object-issue/Object.js:3:1)
    at Module._compile (node:internal/modules/cjs/loader:1364:14)
    at Module._compile (/home/julien/travail/git/babel-object-issue/node_modules/pirates/lib/index.js:117:24)
    at Module._extensions..js (node:internal/modules/cjs/loader:1422:10)
    at Object.newLoader [as .js] (/home/julien/travail/git/babel-object-issue/node_modules/pirates/lib/index.js:121:7)
    at Module.load (node:internal/modules/cjs/loader:1203:32)
    at Function.Module._load (node:internal/modules/cjs/loader:1019:12)
    at Function.runMain (node:internal/modules/run_main:128:12)
    at Object.<anonymous> (/home/julien/travail/git/babel-object-issue/node_modules/@babel/node/src/_babel-node.ts:228:12)
    at Module._compile (node:internal/modules/cjs/loader:1364:14)
    at Object.Module._extensions..js (node:internal/modules/cjs/loader:1422:10)
    at Module.load (node:internal/modules/cjs/loader:1203:32)
    at Function.Module._load (node:internal/modules/cjs/loader:1019:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:128:12)
    at node:internal/main/run_main_module:28:49
```

The problem is that the same file defines another Object class that shadows the
standard class.

Reported in https://github.com/babel/babel/issues/16601
