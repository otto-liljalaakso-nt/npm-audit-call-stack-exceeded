## npm audit crash

This repository contains a reproducer for a bug where the following command crashes:

```
npm audit fix --workspaces --include-workspace-root --force
```

### Usage

1. Clone the repository
2. Install dependencies: `$ npm install`
3. Run audit: `$ npm audit fix --workspaces --include-workspace-root --force`

#### Expected result
Audit completes normally,
potentially modifying `package.json` and `package-lock.json`.

#### Actual result
The following error is printed:

```
...
npm WARN audit Updating react-scripts to 5.0.0,which is a SemVer major change.
Exception in PromiseRejectCallback:snano: WARN audit Updating react-scripts to 5.0.0,which is a SemVer major change.
/home/otto/.volta/tools/image/npm/8.5.4/node_modules/@npmcli/arborist/lib/arborist/build-ideal-tree.js:1067
    return this[_buildDepStep]()

RangeError: Maximum call stack size exceeded
npm ERR! Maximum call stack size exceeded

npm ERR! A complete log of this run can be found in:
npm ERR!     /home/otto/.npm/_logs/2022-03-31T14_27_52_652Z-debug-0.log```

### Logs from a run

Directory `logs` contains logs from a run where the issue was reproduced.

Tool versions were:

* Node 14.15.4
* npm 8.5.4
