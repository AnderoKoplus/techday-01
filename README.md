# Experiments with docker

## setup dev environment
```
$ nvm use 16.13.1
Now using node v16.13.1 (64-bit)
```

## create project
```
$ yarn create next-app .
yarn create v1.22.17
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Installed "create-next-app@12.1.6" with binaries:
      - create-next-app
[##] 2/2Creating a new Next.js app in D:\projects\techday\docker-multi-stage\00-initial.

Using yarn.

Installing dependencies:
- react
- react-dom
- next

yarn add v1.22.17
info No lockfile found.
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 13 new dependencies.
info Direct dependencies
├─ next@12.1.6
├─ react-dom@18.1.0
└─ react@18.1.0
info All dependencies
├─ @next/env@12.1.6
├─ @next/swc-win32-x64-msvc@12.1.6
├─ caniuse-lite@1.0.30001338
├─ js-tokens@4.0.0
├─ nanoid@3.3.4
├─ next@12.1.6
├─ picocolors@1.0.0
├─ postcss@8.4.5
├─ react-dom@18.1.0
├─ react@18.1.0
├─ scheduler@0.22.0
├─ source-map-js@1.0.2
└─ styled-jsx@5.0.2
Done in 4.48s.

Installing devDependencies:
- eslint
- eslint-config-next

yarn add v1.22.17
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
warning "eslint-config-next > @typescript-eslint/parser > @typescript-eslint/typescript-estree > tsutils@3.21.0" has unmet peer dependency "typescript@>=2.8.0 || >= 3.2.0-dev || >= 3.3.0-dev || >= 3.4.0-dev || >= 3.5.0-dev || >= 3.6.0-dev || >= 3.6.0-beta || >= 3.7.0-dev
 || >= 3.7.0-beta".
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 157 new dependencies.
info Direct dependencies
├─ eslint-config-next@12.1.6
└─ eslint@8.15.0
info All dependencies
├─ @babel/runtime-corejs3@7.17.9
├─ @babel/runtime@7.17.9
├─ @eslint/eslintrc@1.2.3
├─ @humanwhocodes/config-array@0.9.5
├─ @humanwhocodes/object-schema@1.2.1
├─ @next/eslint-plugin-next@12.1.6
├─ @nodelib/fs.scandir@2.1.5
├─ @nodelib/fs.stat@2.0.5
├─ @nodelib/fs.walk@1.2.8
├─ @rushstack/eslint-patch@1.1.3
├─ @types/json5@0.0.29
├─ @typescript-eslint/parser@5.22.0
├─ @typescript-eslint/scope-manager@5.22.0
├─ @typescript-eslint/typescript-estree@5.22.0
├─ acorn-jsx@5.3.2
├─ acorn@8.7.1
├─ ajv@6.12.6
├─ ansi-regex@5.0.1
├─ ansi-styles@4.3.0
├─ argparse@2.0.1
├─ aria-query@4.2.2
├─ array-union@2.1.0
├─ array.prototype.flat@1.3.0
├─ array.prototype.flatmap@1.3.0
├─ ast-types-flow@0.0.7
├─ axe-core@4.4.1
├─ axobject-query@2.2.0
├─ balanced-match@1.0.2
├─ brace-expansion@1.1.11
├─ braces@3.0.2
├─ callsites@3.1.0
├─ chalk@4.1.2
├─ color-convert@2.0.1
├─ color-name@1.1.4
├─ concat-map@0.0.1
├─ core-js-pure@3.22.4
├─ cross-spawn@7.0.3
├─ damerau-levenshtein@1.0.8
├─ deep-is@0.1.4
├─ dir-glob@3.0.1
├─ emoji-regex@9.2.2
├─ es-to-primitive@1.2.1
├─ escape-string-regexp@4.0.0
├─ eslint-config-next@12.1.6
├─ eslint-import-resolver-typescript@2.7.1
├─ eslint-module-utils@2.7.3
├─ eslint-plugin-import@2.26.0
├─ eslint-plugin-jsx-a11y@6.5.1
├─ eslint-plugin-react-hooks@4.5.0
├─ eslint-plugin-react@7.29.4
├─ eslint-scope@7.1.1
├─ eslint-utils@3.0.0
├─ eslint-visitor-keys@3.3.0
├─ eslint@8.15.0
├─ esquery@1.4.0
├─ esrecurse@4.3.0
├─ estraverse@5.3.0
├─ fast-deep-equal@3.1.3
├─ fast-glob@3.2.11
├─ fast-json-stable-stringify@2.1.0
├─ fast-levenshtein@2.0.6
├─ fastq@1.13.0
├─ file-entry-cache@6.0.1
├─ fill-range@7.0.1
├─ find-up@2.1.0
├─ flat-cache@3.0.4
├─ flatted@3.2.5
├─ function.prototype.name@1.1.5
├─ functional-red-black-tree@1.0.1
├─ get-symbol-description@1.0.0
├─ glob-parent@6.0.2
├─ glob@7.2.0
├─ globals@13.13.0
├─ globby@11.1.0
├─ has-bigints@1.0.2
├─ has-flag@4.0.0
├─ import-fresh@3.3.0
├─ imurmurhash@0.1.4
├─ is-bigint@1.0.4
├─ is-boolean-object@1.1.2
├─ is-callable@1.2.4
├─ is-core-module@2.9.0
├─ is-date-object@1.0.5
├─ is-extglob@2.1.1
├─ is-glob@4.0.3
├─ is-negative-zero@2.0.2
├─ is-number-object@1.0.7
├─ is-number@7.0.0
├─ is-regex@1.1.4
├─ is-shared-array-buffer@1.0.2
├─ is-string@1.0.7
├─ is-symbol@1.0.4
├─ is-weakref@1.0.2
├─ isexe@2.0.0
├─ json-schema-traverse@0.4.1
├─ json-stable-stringify-without-jsonify@1.0.1
├─ json5@1.0.1
├─ jsx-ast-utils@3.3.0
├─ language-subtag-registry@0.3.21
├─ language-tags@1.0.5
├─ locate-path@2.0.0
├─ lodash.merge@4.6.2
├─ lru-cache@6.0.0
├─ merge2@1.4.1
├─ micromatch@4.0.5
├─ minimist@1.2.6
├─ ms@2.1.2
├─ natural-compare@1.4.0
├─ object-assign@4.1.1
├─ object-inspect@1.12.0
├─ object.entries@1.1.5
├─ object.fromentries@2.0.5
├─ object.hasown@1.1.1
├─ optionator@0.9.1
├─ p-limit@1.3.0
├─ p-locate@2.0.0
├─ p-try@1.0.0
├─ parent-module@1.0.1
├─ path-exists@3.0.0
├─ path-key@3.1.1
├─ path-parse@1.0.7
├─ path-type@4.0.0
├─ picomatch@2.3.1
├─ prop-types@15.8.1
├─ punycode@2.1.1
├─ queue-microtask@1.2.3
├─ react-is@16.13.1
├─ regexpp@3.2.0
├─ resolve-from@4.0.0
├─ reusify@1.0.4
├─ rimraf@3.0.2
├─ run-parallel@1.2.0
├─ semver@6.3.0
├─ shebang-command@2.0.0
├─ shebang-regex@3.0.0
├─ slash@3.0.0
├─ string.prototype.matchall@4.0.7
├─ string.prototype.trimend@1.0.5
├─ string.prototype.trimstart@1.0.5
├─ strip-ansi@6.0.1
├─ strip-bom@3.0.0
├─ strip-json-comments@3.1.1
├─ supports-color@7.2.0
├─ supports-preserve-symlinks-flag@1.0.0
├─ text-table@0.2.0
├─ to-regex-range@5.0.1
├─ tslib@1.14.1
├─ tsutils@3.21.0
├─ type-check@0.4.0
├─ type-fest@0.20.2
├─ unbox-primitive@1.0.2
├─ uri-js@4.4.1
├─ v8-compile-cache@2.3.0
├─ which-boxed-primitive@1.0.2
├─ which@2.0.2
├─ word-wrap@1.2.3
└─ yallist@4.0.0
Done in 8.53s.

Initialized a git repository.

Success! Created test at D:\projects\techday\docker-multi-stage\00-initial
Inside that directory, you can run several commands:

  yarn dev
    Starts the development server.

  yarn build
    Builds the app for production.

  yarn start
    Runs the built app in production mode.

We suggest that you begin by typing:

  cd D:\projects\techday\docker-multi-stage\00-initial
  yarn dev

Done in 16.18s.
```

```
## build project

$ yarn build
yarn run v1.22.17
$ next build
info  - Checking validity of types
info  - Creating an optimized production build
info  - Compiled successfully
info  - Collecting page data
info  - Generating static pages (3/3)
info  - Finalizing page optimization

Page                                       Size     First Load JS
┌ ○ /                                      6.25 kB        81.2 kB
├   └ css/149b18973e5508c7.css             655 B
├   /_app                                  0 B            74.9 kB
├ ○ /404                                   193 B          75.1 kB
└ λ /api/hello                             0 B            74.9 kB
+ First Load JS shared by all              74.9 kB
  ├ chunks/framework-1f10003e17636e37.js   45 kB
  ├ chunks/main-fc7d2f0e2098927e.js        28.7 kB
  ├ chunks/pages/_app-69da446bea935969.js  493 B
  ├ chunks/webpack-69bfa6990bb9e155.js     769 B
  └ css/27d177a30947857b.css               194 B

λ  (Server)  server-side renders at runtime (uses getInitialProps or getServerSideProps)
○  (Static)  automatically rendered as static HTML (uses no initial props)

Done in 10.54s.
```

## things i tried
1. [Initial docker setup](00-initial/README.md)
2. [Switch yarn to production](01-yarn-production/README.md)
3. [Use docker multi-stage build](02-docker-multi-stage-build/README.md)
4. [Experimental NextJS standalone mode](03-nextjs-standalone/README.md)
5. [Experimental docker --squash squash](04-squash/README.md)
6. use .dockerignore - works like .gitignore but for docker
7. [dive](https://github.com/wagoodman/dive) - explore docker images with ascii gui

## results

| image                             |    size |
|:----------------------------------|--------:|
| 02-docker-multi-stage-build-cp-sq |   111MB |
| 02-docker-multi-stage-build-cp    |   112MB |
| 03-nextjs-standalone-sq           |   117MB |
| 03-nextjs-standalone              |   118MB |
| 02-docker-multi-stage-build-sq    |   217MB |
| 02-docker-multi-stage-build       |   218MB |
| 01-yarn-production-sq             |  1.76GB |
| 00-initial-sq                     |  1.76GB |
| 01-yarn-production                |  1.77GB |
| 00-initial                        |  1.94GB |

* sq - squash
* cp - cherry-pick
* min max size difference is 17.4x :)
