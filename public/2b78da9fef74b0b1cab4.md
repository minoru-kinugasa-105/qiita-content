---
title: >-
  【Node v24】jsonwebtokenで発生する Cannot read properties of undefined (reading
  'prototype') エラーの解決
tags:
  - Node.js
  - nextauth.js
  - jsonwebtoken
private: false
updated_at: '2025-05-09T19:26:14+09:00'
id: 2b78da9fef74b0b1cab4
organization_url_name: null
slide: false
ignorePublish: false
---

# 概要
`jsonwebtoken`libが `Node v24`で動作せず、
`buffer-equal-constant-time` ライブラリがエラーを投げてしまう.

```js
var origSlowBufEqual = SlowBuffer.prototype.equal;
                                  ^

TypeError: Cannot read properties of undefined (reading 'prototype')
    at Object.<anonymous> (/Users/user/testnode24/node_modules/buffer-equal-constant-time/index.js:37:35)
    at Module._compile (node:internal/modules/cjs/loader:1734:14)
    at Object..js (node:internal/modules/cjs/loader:1899:10)
    at Module.load (node:internal/modules/cjs/loader:1469:32)
    at Module._load (node:internal/modules/cjs/loader:1286:12)
    at TracingChannel.traceSync (node:diagnostics_channel:322:14)
    at wrapModuleLoad (node:internal/modules/cjs/loader:235:24)
    at Module.require (node:internal/modules/cjs/loader:1491:12)
    at require (node:internal/modules/helpers:135:16)
    at Object.<anonymous> (/Users/user/testnode24/node_modules/jwa/index.js:1:19)

Node.js v24.0.0
```

---

また、Auth.js (NextAuth.js)内 `auth.ts`などにおいて
クライアントサイドで`jsonwebtoken`を使用しようとすることによりエラーが投げられてしまう.

```js
 GET /api/auth/session 500 in 470ms
 
 ⨯ TypeError: Cannot read properties of undefined (reading 'prototype')
    at __webpack_require__ (.next/server/webpack-runtime.js:33:43)
    at __webpack_require__ (.next/server/webpack-runtime.js:33:43)
    at __webpack_require__ (.next/server/webpack-runtime.js:33:43)
    at __webpack_require__ (.next/server/webpack-runtime.js:33:43)
    at __webpack_require__ (.next/server/webpack-runtime.js:33:43)
    at __webpack_require__ (.next/server/webpack-runtime.js:33:43)
    at eval (webpack-internal:///(rsc)/./src/auth.ts:14:70)
    at __webpack_require__.a (.next/server/webpack-runtime.js:105:13)
    at eval (webpack-internal:///(rsc)/./src/auth.ts:1:21)
    at <unknown> (rsc)/./src/auth.ts (/Users/user/project/client/.next/server/app/api/auth/[...nextauth]/route.js:54:1)
    at __webpack_require__ (.next/server/webpack-runtime.js:33:43)
    at eval (webpack-internal:///(rsc)/./src/app/api/auth/[...nextauth]/route.ts:7:63)
    at __webpack_require__.a (.next/server/webpack-runtime.js:105:13)
    at eval (webpack-internal:///(rsc)/./src/app/api/auth/[...nextauth]/route.ts:1:21)
    at <unknown> (rsc)/./src/app/api/auth/[...nextauth]/route.ts (/Users/user/project/client/.next/server/app/api/auth/[...nextauth]/route.js:43:1)
    at __webpack_require__ (.next/server/webpack-runtime.js:33:43)
    at __webpack_require__.a (.next/server/webpack-runtime.js:105:13)
    at __webpack_require__ (.next/server/webpack-runtime.js:33:43)
    at __webpack_exec__ (.next/server/app/api/auth/[...nextauth]/route.js:206:39)
    at <unknown> (.next/server/app/api/auth/[...nextauth]/route.js:207:714)
    at __webpack_require__.X (.next/server/webpack-runtime.js:237:21)
    at <unknown> (.next/server/app/api/auth/[...nextauth]/route.js:207:47)
    at Object.<anonymous> (.next/server/app/api/auth/[...nextauth]/route.js:210:3) {
  page: '/api/auth/session'
}
```

# 原因
`jsonwebtoken` が依存している `jws` が依存している `jwa` lib内で
`SlowBuffer.prototype.equal`を用いてバッファ比較が行われますが、
`NodeJS v24.0.0`のリリースでこのAPIが削除されたため動作できなかったことが原因です.

# 修正方法
`jwa`においてパッチ版がリリースされたため、以下にバージョンを合わせた上で
`npm i`（またはプロジェクトの依存再構築cmd）を実行することで解決できます。

```ts:package.json
"dependencies": {
    "jsonwebtoken": "^9.0.2",
    "jws": "^3.2.2",
    "jwa": "^1.4.2"
}
```

# 参照
> auth0 / node-jsonwebtoken Issue
> https://github.com/auth0/node-jsonwebtoken/issues/992
