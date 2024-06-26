# Changelog

## 5.3.2

- Updated to SQLCipher 4.5.2 / SQLite 3.39.2
- Updated rest of code from upstream node-sqlite3 repo
- MacOS: Updated to OpenSSL 1.1.1s
- Windows: Updated to OpenSSL 3.0.7
- Switch CI to GitHub Actions
- Updated all npm dependencies

## 5.3.1

- Linux: Downgrade glibc requirement to 2.24, supporting Ubuntu 16.10+ and Debian 9 (Stretch)+ again.

## 5.3.0

- Pre-built binaries for macos/darwin arm64.
- Add typescript types.
- Don't fallback to building from source.
- Smaller NPM package (build dependencies not included anymore).
- Linux: Requires glibc 2.28+ (Ubuntu 18.10+).

## 5.2.0

- Statically link OpenSSL on Linux and Windows, in addition to MacOS. No more DLLs distributed.
- Upgrade to OpenSSL 1.1.1i.
- Provide pre-built binaries for ARM64 on Windows (not regularly tested, but should work).

## 5.1.0

- Update to SQLCipher 4.4.2 / SQLite 3.33.0.
- Fix crash on Electron on Windows.
- Always use system or bundled OpenSSL, not OpenSSL bundled with Node.

## 5.0.0

- Major change: Use N-API instead of NAN.
  This removes the need to have separate Node binaries for each Node and Electron version, which was the most common cause of reported issues. 
- Update to SQLCipher 4.4.0 / SQLite 3.31.0.
- Drop support for Node < 10, and Electron < 6.

Includes these upstream changes from mapbox/node-sqlite3:

5.0.1
- dep: node-addon-api to ^3.0.0 [#1367](https://github.com/mapbox/node-sqlite3/pull/1367)
- bug: bad comparison of c string [#1347](https://github.com/mapbox/node-sqlite3/pull/1347)
- bug: worker threads crash [#1367](https://github.com/mapbox/node-sqlite3/pull/1367)
- bug: segfaults [#1368](https://github.com/mapbox/node-sqlite3/pull/1368)
- typo: broken link to MapBox site [#1369](https://github.com/mapbox/node-sqlite3/pull/1369)

5.0.0
- prebuilt: Node 14 support, dropped support for all version of Node < 10 [#1304](https://github.com/mapbox/node-sqlite3/pull/1304)
- napi: refactor codebase to use N-API instead of NAN (+ various improvements) [#1304](https://github.com/mapbox/node-sqlite3/pull/1304)
- trace: don't require throw to add trace info for verbose [#1317](https://github.com/mapbox/node-sqlite3/pull/1317)

4.2.0
- webpack: split sqlite3-binding.js out so that it could be override by webpack [#1268](https://github.com/mapbox/node-sqlite3/pull/1268)
- sqlite3: enable 'SQLITE_ENABLE_DBSTAT_VTAB=1' [#1281](https://github.com/mapbox/node-sqlite3/pull/1281)
- deps: remove request [#1287](https://github.com/mapbox/node-sqlite3/pull/1287)
- electron: fix dist url [#1282](https://github.com/mapbox/node-sqlite3/pull/1282)

4.1.0
- https everywhere [#1177](https://github.com/mapbox/node-sqlite3/pull/1177)


## 4.1.0

- Update to SQLCipher 4.3.0 / SQLite 3.30.1.

## 4.0.0

- Update to SQLCipher 4.2.0 / SQLite 3.28.0.

## 3.2.1

- Publish more prebuilt binaries.

## 3.2.0

- Update to SQLCipher 3.4.1 / SQLite 3.20.1.
- Also bundle msvcr120.dll

## 3.1.16

- First release of the fork, based on SQLCipher 3.4.1 / SQLite 3.15.2.
