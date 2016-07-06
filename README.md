# debug-eslint-plugin-import

This repository demonstrates a bug in eslint-plugin-import and/or
eslint-plugin-meteor when run under NPM 3.9.6 and Node 0.10.45

To duplicate the problem, simply
 - `git clone ` this repository
 - `nvm install 0.10.45`
 - `npm install -g npm@3.9.6` (if nvm left npm at some other version)
 - `npm install`
 - `npm run lint`

If you run other versions of npm to see working scenarios, be sure to
 - `rm -rf node-modules` and
 - `npm install` 

again so as to not mix your tests

Below is an example of the bad output
```
rhett@dreamshot:~/oob/meteors/debug-eslint-plugin-import$ ls -l
total 8
-rw-rw-r-- 1 rhett rhett 558 Jul  5 16:03 package.json
-rw-rw-r-- 1 rhett rhett   0 Jul  6 10:05 README.md
-rw-rw-r-- 1 rhett rhett  14 Jul  5 13:56 sample.js
rhett@dreamshot:~/oob/meteors/debug-eslint-plugin-import$ nvm install 0.10.45
v0.10.45 is already installed.
Now using node v0.10.45 (npm v3.9.6)
rhett@dreamshot:~/oob/meteors/debug-eslint-plugin-import$ npm install
/home/rhett/oob/meteors/debug-eslint-plugin-import
├─┬ eslint@2.13.1
│ ├─┬ chalk@1.1.3
│ │ ├── ansi-styles@2.2.1
│ │ ├── escape-string-regexp@1.0.5
│ │ ├── has-ansi@2.0.0
│ │ ├── strip-ansi@3.0.1
│ │ └── supports-color@2.0.0
│ ├─┬ concat-stream@1.5.1
│ │ ├── inherits@2.0.1
│ │ ├─┬ readable-stream@2.0.6
│ │ │ ├── core-util-is@1.0.2
│ │ │ ├── process-nextick-args@1.0.7
│ │ │ ├── string_decoder@0.10.31
│ │ │ └── util-deprecate@1.0.2
│ │ └── typedarray@0.0.6
│ ├─┬ debug@2.2.0
│ │ └── ms@0.7.1
│ ├─┬ doctrine@1.2.2
│ │ ├── esutils@1.1.6
│ │ └── isarray@1.0.0
│ ├─┬ es6-map@0.1.4
│ │ ├── d@0.1.1
│ │ ├── es5-ext@0.10.12
│ │ ├── es6-iterator@2.0.0
│ │ └── event-emitter@0.3.4
│ ├─┬ escope@3.6.0
│ │ ├── es6-weak-map@2.0.1
│ │ └─┬ esrecurse@4.1.0
│ │   └── estraverse@4.1.1
│ ├─┬ espree@3.1.6
│ │ ├── acorn@3.2.0
│ │ └── acorn-jsx@3.0.1
│ ├── estraverse@4.2.0
│ ├── esutils@2.0.2
│ ├─┬ file-entry-cache@1.2.4
│ │ └─┬ flat-cache@1.0.10
│ │   ├─┬ del@2.2.1
│ │   │ ├─┬ globby@5.0.0
│ │   │ │ ├─┬ array-union@1.0.2
│ │   │ │ │ └── array-uniq@1.0.3
│ │   │ │ └── arrify@1.0.1
│ │   │ ├── is-path-cwd@1.0.0
│ │   │ ├─┬ is-path-in-cwd@1.0.0
│ │   │ │ └── is-path-inside@1.0.0
│ │   │ ├── pify@2.3.0
│ │   │ └── rimraf@2.5.3
│ │   ├── graceful-fs@4.1.4
│ │   ├── read-json-sync@1.1.1
│ │   └── write@0.2.1
│ ├─┬ glob@7.0.5
│ │ ├── fs.realpath@1.0.0
│ │ ├─┬ inflight@1.0.5
│ │ │ └── wrappy@1.0.2
│ │ ├─┬ minimatch@3.0.2
│ │ │ └─┬ brace-expansion@1.1.5
│ │ │   ├── balanced-match@0.4.1
│ │ │   └── concat-map@0.0.1
│ │ └── once@1.3.3
│ ├── globals@9.9.0
│ ├── ignore@3.1.3
│ ├── imurmurhash@0.1.4
│ ├─┬ inquirer@0.12.0
│ │ ├── ansi-escapes@1.4.0
│ │ ├── ansi-regex@2.0.0
│ │ ├─┬ cli-cursor@1.0.2
│ │ │ └─┬ restore-cursor@1.0.1
│ │ │   ├── exit-hook@1.1.1
│ │ │   └── onetime@1.1.0
│ │ ├── cli-width@2.1.0
│ │ ├── figures@1.7.0
│ │ ├─┬ readline2@1.0.1
│ │ │ ├─┬ code-point-at@1.0.0
│ │ │ │ └── number-is-nan@1.0.0
│ │ │ ├── is-fullwidth-code-point@1.0.0
│ │ │ └── mute-stream@0.0.5
│ │ ├── run-async@0.1.0
│ │ ├── rx-lite@3.1.2
│ │ ├── string-width@1.0.1
│ │ └── through@2.3.8
│ ├─┬ is-my-json-valid@2.13.1
│ │ ├── generate-function@2.0.0
│ │ ├─┬ generate-object-property@1.2.0
│ │ │ └── is-property@1.0.2
│ │ ├── jsonpointer@2.0.0
│ │ └── xtend@4.0.1
│ ├─┬ is-resolvable@1.0.0
│ │ └── tryit@1.0.2
│ ├─┬ js-yaml@3.6.1
│ │ ├─┬ argparse@1.0.7
│ │ │ └── sprintf-js@1.0.3
│ │ └── esprima@2.7.2
│ ├─┬ json-stable-stringify@1.0.1
│ │ └── jsonify@0.0.0
│ ├─┬ levn@0.3.0
│ │ ├── prelude-ls@1.1.2
│ │ └── type-check@0.3.2
│ ├── lodash@4.13.1
│ ├─┬ mkdirp@0.5.1
│ │ └── minimist@0.0.8
│ ├─┬ optionator@0.8.1
│ │ ├── deep-is@0.1.3
│ │ ├── fast-levenshtein@1.1.3
│ │ └── wordwrap@1.0.0
│ ├── path-is-absolute@1.0.0
│ ├── path-is-inside@1.0.1
│ ├── pluralize@1.2.1
│ ├── progress@1.1.8
│ ├─┬ require-uncached@1.0.2
│ │ ├─┬ caller-path@0.1.0
│ │ │ └── callsites@0.2.0
│ │ └── resolve-from@1.0.1
│ ├── shelljs@0.6.0
│ ├── strip-json-comments@1.0.4
│ ├─┬ table@3.7.8
│ │ ├── bluebird@3.4.1
│ │ ├── slice-ansi@0.0.4
│ │ ├── tv4@1.2.7
│ │ └── xregexp@3.1.1
│ ├── text-table@0.2.0
│ └─┬ user-home@2.0.0
│   └── os-homedir@1.0.1
├─┬ eslint-config-airbnb@9.0.1
│ └── eslint-config-airbnb-base@3.0.1
├─┬ eslint-import-resolver-meteor@0.2.4
│ ├── object-assign@4.1.0
│ └── resolve@1.1.7
├─┬ eslint-plugin-import@1.10.2
│ ├── builtin-modules@1.1.1
│ ├── contains-path@0.1.0
│ ├── es6-set@0.1.4
│ ├── es6-symbol@3.1.0
│ ├── eslint-import-resolver-node@0.2.1
│ ├─┬ lodash.cond@4.4.0
│ │ ├─┬ lodash._baseiteratee@4.7.0
│ │ │ └── lodash._stringtopath@4.8.0
│ │ └── lodash.rest@4.0.3
│ ├─┬ lodash.endswith@4.1.0
│ │ ├── lodash._basetostring@4.12.0
│ │ └── lodash.tostring@4.1.3
│ ├─┬ lodash.find@4.4.0
│ │ ├── lodash._baseeach@4.1.3
│ │ ├── lodash._basefind@3.0.0
│ │ └── lodash._basefindindex@3.6.0
│ ├── lodash.findindex@4.4.0
│ ├─┬ pkg-dir@1.0.0
│ │ └─┬ find-up@1.1.2
│ │   ├── path-exists@2.1.0
│ │   └─┬ pinkie-promise@2.0.1
│ │     └── pinkie@2.0.4
│ └── pkg-up@1.0.0
├─┬ eslint-plugin-jsx-a11y@1.5.5
│ ├── damerau-levenshtein@1.0.0
│ └── jsx-ast-utils@1.2.1
├─┬ eslint-plugin-meteor@3.6.0
│ ├─┬ babel-polyfill@6.9.0
│ │ ├── babel-regenerator-runtime@6.5.0
│ │ ├─┬ babel-runtime@6.9.2
│ │ │ └── regenerator-runtime@0.9.5
│ │ └── core-js@2.4.0
│ ├─┬ babel-register@6.8.0
│ │ ├─┬ babel-core@6.10.4
│ │ │ ├─┬ babel-code-frame@6.11.0
│ │ │ │ └── js-tokens@2.0.0
│ │ │ ├─┬ babel-generator@6.11.0
│ │ │ │ ├── babel-runtime@6.9.2
│ │ │ │ └─┬ detect-indent@3.0.1
│ │ │ │   ├── get-stdin@4.0.1
│ │ │ │   ├── minimist@1.2.0
│ │ │ │   └─┬ repeating@1.1.3
│ │ │ │     └── is-finite@1.0.1
│ │ │ ├── babel-helpers@6.8.0
│ │ │ ├── babel-messages@6.8.0
│ │ │ ├── babel-register@6.9.0
│ │ │ ├── babel-runtime@6.9.2
│ │ │ ├─┬ babel-template@6.9.0
│ │ │ │ └── babel-runtime@6.9.2
│ │ │ ├─┬ babel-traverse@6.10.4
│ │ │ │ ├── babel-runtime@6.9.2
│ │ │ │ └── globals@8.18.0
│ │ │ ├─┬ babel-types@6.11.1
│ │ │ │ ├── babel-runtime@6.9.2
│ │ │ │ └── to-fast-properties@1.0.2
│ │ │ ├── babylon@6.8.3
│ │ │ ├── convert-source-map@1.2.0
│ │ │ ├── json5@0.4.0
│ │ │ ├── path-exists@1.0.0
│ │ │ ├── private@0.1.6
│ │ │ ├── shebang-regex@1.0.0
│ │ │ ├── slash@1.0.0
│ │ │ └── source-map@0.5.6
│ │ ├─┬ home-or-tmp@1.0.0
│ │ │ ├── os-tmpdir@1.0.1
│ │ │ └── user-home@1.1.1
│ │ ├── lodash@3.10.1
│ │ ├── path-exists@1.0.0
│ │ └─┬ source-map-support@0.2.10
│ │   └─┬ source-map@0.1.32
│ │     └── amdefine@1.0.0
│ ├── babel-runtime@6.6.1
│ ├─┬ invariant@2.2.1
│ │ └─┬ loose-envify@1.2.0
│ │   └── js-tokens@1.0.3
│ ├─┬ lodash.memoize@4.1.0
│ │ └── lodash._root@3.0.1
│ └── path-exists@3.0.0
└── eslint-plugin-react@5.2.2

npm WARN debug-eslint-plugin-import No description
npm WARN debug-eslint-plugin-import No repository field.
npm WARN debug-eslint-plugin-import No license field.
rhett@dreamshot:~/oob/meteors/debug-eslint-plugin-import$ npm run lint

> @ lint /home/rhett/oob/meteors/debug-eslint-plugin-import
> eslint .

Property 'Symbol(Symbol.iterator)_9.uun1imjhy6uyds4i' of object [object Map] is not a function
TypeError: Property 'Symbol(Symbol.iterator)_9.uun1imjhy6uyds4i' of object [object Map] is not a function
    at EventEmitter.ProgramExit (/home/rhett/oob/meteors/debug-eslint-plugin-import/node_modules/eslint-plugin-import/lib/rules/export.js:93:149)
    at EventEmitter.emit (events.js:117:20)
    at NodeEventGenerator.leaveNode (/home/rhett/oob/meteors/debug-eslint-plugin-import/node_modules/eslint/lib/util/node-event-generator.js:49:22)
    at CodePathAnalyzer.leaveNode (/home/rhett/oob/meteors/debug-eslint-plugin-import/node_modules/eslint/lib/code-path-analysis/code-path-analyzer.js:627:23)
    at CommentEventGenerator.leaveNode (/home/rhett/oob/meteors/debug-eslint-plugin-import/node_modules/eslint/lib/util/comment-event-generator.js:110:23)
    at Controller.traverser.traverse.leave (/home/rhett/oob/meteors/debug-eslint-plugin-import/node_modules/eslint/lib/eslint.js:908:36)
    at Controller.__execute (/home/rhett/oob/meteors/debug-eslint-plugin-import/node_modules/estraverse/estraverse.js:397:31)
    at Controller.traverse (/home/rhett/oob/meteors/debug-eslint-plugin-import/node_modules/estraverse/estraverse.js:491:28)
    at Controller.Traverser.controller.traverse (/home/rhett/oob/meteors/debug-eslint-plugin-import/node_modules/eslint/lib/util/traverser.js:36:33)
    at EventEmitter.module.exports.api.verify (/home/rhett/oob/meteors/debug-eslint-plugin-import/node_modules/eslint/lib/eslint.js:902:23)

npm ERR! Linux 4.4.0-28-generic
npm ERR! argv "node" "/home/rhett/.nvm/v0.10.45/bin/npm" "run" "lint"
npm ERR! node v0.10.45
npm ERR! npm  v3.9.6
npm ERR! code ELIFECYCLE
npm ERR! @ lint: `eslint .`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the @ lint script 'eslint .'.
npm ERR! Make sure you have the latest version of node.js and npm installed.
npm ERR! If you do, this is most likely a problem with the  package,
npm ERR! not with npm itself.
npm ERR! Tell the author that this fails on your system:
npm ERR!     eslint .
npm ERR! You can get information on how to open an issue for this project with:
npm ERR!     npm bugs
npm ERR! Or if that isn't available, you can get their info via:
npm ERR!     npm owner ls
npm ERR! There is likely additional logging output above.

npm ERR! Please include the following file with any support request:
npm ERR!     /home/rhett/oob/meteors/debug-eslint-plugin-import/npm-debug.log

```
