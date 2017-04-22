# npmdoc-geoip-lite

#### api documentation for  [geoip-lite (v1.2.0)](https://github.com/bluesmoon/node-geoip)  [![npm package](https://img.shields.io/npm/v/npmdoc-geoip-lite.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-geoip-lite) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-geoip-lite.svg)](https://travis-ci.org/npmdoc/node-npmdoc-geoip-lite)

#### A light weight native JavaScript implementation of GeoIP API from MaxMind

[![NPM](https://nodei.co/npm/geoip-lite.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/geoip-lite)

- [https://npmdoc.github.io/node-npmdoc-geoip-lite/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-geoip-lite/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-geoip-lite/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-geoip-lite/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-geoip-lite/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-geoip-lite/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Philip Tellis",
        "url": "http://bluesmoon.info/"
    },
    "bugs": {
        "url": "https://github.com/bluesmoon/node-geoip/issues"
    },
    "config": {
        "update": true
    },
    "contributors": [
        {
            "name": "Philip Tellis",
            "url": "http://bluesmoon.info/"
        }
    ],
    "dependencies": {
        "async": "^2.1.1",
        "colors": "^1.1.2",
        "glob": "^7.1.1",
        "iconv-lite": "^0.4.13",
        "lazy": "^1.0.11",
        "rimraf": "^2.5.2",
        "unzip": "^0.1.11"
    },
    "description": "A light weight native JavaScript implementation of GeoIP API from MaxMind",
    "devDependencies": {
        "nodeunit": "^0.10.2"
    },
    "directories": {},
    "dist": {
        "shasum": "d55369bd6b34132e11cb2f7fc519942bbe24245d",
        "tarball": "https://registry.npmjs.org/geoip-lite/-/geoip-lite-1.2.0.tgz"
    },
    "engines": {
        "node": ">=5.10.0"
    },
    "files": [
        "lib/",
        "data/",
        "test/",
        "scripts/"
    ],
    "gitHead": "0cf9a6b441ca91dad3c0fcb3fd0e07180b28f0c8",
    "homepage": "https://github.com/bluesmoon/node-geoip",
    "keywords": [
        "geo",
        "geoip",
        "ip",
        "ipv4",
        "ipv6",
        "geolookup",
        "maxmind",
        "geolite"
    ],
    "license": "Apache-2.0",
    "main": "lib/geoip.js",
    "maintainers": [
        {
            "name": "bluesmoon"
        }
    ],
    "name": "geoip-lite",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git://github.com/bluesmoon/node-geoip.git"
    },
    "scripts": {
        "test": "nodeunit --reporter=minimal test/tests.js",
        "updatedb": "node scripts/updatedb.js",
        "updatedb-debug": "node scripts/updatedb.js debug"
    },
    "version": "1.2.0",
    "bin": {}
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
