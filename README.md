Fork of [node-sqlite3](https://github.com/mapbox/node-sqlite3), modified to use [SQLCipher](https://www.zetetic.net/sqlcipher/).

While the `node-sqlite3` project does include support for compiling against sqlcipher, it requires manual work, and does not work out-of-the-box on Electron on Windows. This fork changes the default configuration to bundle SQLCipher directly, as well as OpenSSL where required.

## Supported platforms

Binaries are built against N-API 3 and 6, on MacOS, Windows (ia32 and x64) and Linux (x64).

Node 10+ and Electron 6+ is supported.

Other platforms/architectures may work by building from source - see the section below.

# Installation

```sh
yarn add "@journeyapps/sqlcipher"
# Or: npm install --save "@journeyapps/sqlcipher"
```

# Usage

``` js
var sqlite3 = require('@journeyapps/sqlcipher').verbose();
var db = new sqlite3.Database('test.db');

db.serialize(function() {
  // This is the default, but it is good to specify explicitly:
  db.run("PRAGMA cipher_compatibility = 4");

  // To open a database created with SQLCipher 3.x, use this:
  // db.run("PRAGMA cipher_compatibility = 3");

  db.run("PRAGMA key = 'mysecret'");
  db.run("CREATE TABLE lorem (info TEXT)");

  var stmt = db.prepare("INSERT INTO lorem VALUES (?)");
  for (var i = 0; i < 10; i++) {
      stmt.run("Ipsum " + i);
  }
  stmt.finalize();

  db.each("SELECT rowid AS id, info FROM lorem", function(err, row) {
      console.log(row.id + ": " + row.info);
  });
});

db.close();
```

# SQLCipher

A copy of the source for SQLCipher 4.5.2 is bundled, which is based on SQLite 3.39.2.

## Building from source

Building from source when installing the package is only supported up to version 5.2.0.

The two pre-built versions (N-API 3 and N-API 6) cover all electron and node versions, so building from source should
not be required.

## OpenSSL

SQLCipher depends on OpenSSL.

For Windows, we bundle OpenSSL 3.0.7. Binaries are generated using [vckpg](https://github.com/microsoft/vcpkg) (e.g., `.\vcpkg\vcpkg install openssl:x64-windows-static`).

On Mac we bundle OpenSSL 1.1.1s.

On Linux we dynamically link against the system OpenSSL.

# API

See the [API documentation](https://github.com/mapbox/node-sqlite3/wiki) in the wiki.

Documentation for the SQLCipher extension is available [here](https://www.zetetic.net/sqlcipher/sqlcipher-api/).

# Acknowledgments

Most of the work in this library is from the [node-sqlite3](https://github.com/mapbox/node-sqlite3) library by [MapBox](https://mapbox.com/).

Additionally, some of the SQLCipher-related changes are based on a fork by [liubiggun](https://github.com/liubiggun/node-sqlite3).

# License

`node-sqlcipher` is [BSD licensed](./LICENSE).

`SQLCipher` is `Copyright (c) 2016, ZETETIC LLC` under the [BSD license](https://github.com/sqlcipher/sqlcipher/blob/master/LICENSE).

`SQLite` is Public Domain
