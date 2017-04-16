# api documentation for  [geoip-lite (v1.2.0)](https://github.com/bluesmoon/node-geoip)  [![npm package](https://img.shields.io/npm/v/npmdoc-geoip-lite.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-geoip-lite) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-geoip-lite.svg)](https://travis-ci.org/npmdoc/node-npmdoc-geoip-lite)
#### A light weight native JavaScript implementation of GeoIP API from MaxMind

[![NPM](https://nodei.co/npm/geoip-lite.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/geoip-lite)

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
    "version": "1.2.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module geoip-lite](#apidoc.module.geoip-lite)
1.  [function <span class="apidocSignatureSpan">geoip-lite.</span>cmp (a, b)](#apidoc.element.geoip-lite.cmp)
1.  [function <span class="apidocSignatureSpan">geoip-lite.</span>lookup (ip)](#apidoc.element.geoip-lite.lookup)
1.  [function <span class="apidocSignatureSpan">geoip-lite.</span>pretty (n)](#apidoc.element.geoip-lite.pretty)
1.  [function <span class="apidocSignatureSpan">geoip-lite.</span>startWatchingDataUpdate (callback)](#apidoc.element.geoip-lite.startWatchingDataUpdate)
1.  [function <span class="apidocSignatureSpan">geoip-lite.</span>stopWatchingDataUpdate ()](#apidoc.element.geoip-lite.stopWatchingDataUpdate)
1.  object <span class="apidocSignatureSpan">geoip-lite.</span>fsWatcher

#### [module geoip-lite.fsWatcher](#apidoc.module.geoip-lite.fsWatcher)
1.  [function <span class="apidocSignatureSpan">geoip-lite.fsWatcher.</span>makeFsWatchFilter (name, directory, filename, cooldownDelay, callback)](#apidoc.element.geoip-lite.fsWatcher.makeFsWatchFilter)
1.  [function <span class="apidocSignatureSpan">geoip-lite.fsWatcher.</span>stopWatching (name)](#apidoc.element.geoip-lite.fsWatcher.stopWatching)



# <a name="apidoc.module.geoip-lite"></a>[module geoip-lite](#apidoc.module.geoip-lite)

#### <a name="apidoc.element.geoip-lite.cmp"></a>[function <span class="apidocSignatureSpan">geoip-lite.</span>cmp (a, b)](#apidoc.element.geoip-lite.cmp)
- description and source-code
```javascript
cmp = function (a, b) {
  if (typeof a === 'number' && typeof b === 'number') {
    return (a < b ? -1 : (a > b ? 1 : 0));
  }

  if (a instanceof Array && b instanceof Array) {
    return this.cmp6(a, b);
  }

  return null;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.geoip-lite.lookup"></a>[function <span class="apidocSignatureSpan">geoip-lite.</span>lookup (ip)](#apidoc.element.geoip-lite.lookup)
- description and source-code
```javascript
lookup = function (ip) {
		if (!ip) {
			return null;
		} else if (typeof ip === 'number') {
			return lookup4(ip);
		} else if (net.isIP(ip) === 4) {
			return lookup4(utils.aton4(ip));
		} else if (net.isIP(ip) === 6) {
			var ipv4 = get4mapped(ip);
			if (ipv4) {
				return lookup4(utils.aton4(ipv4));
			} else {
				return lookup6(utils.aton6(ip));
			}
		}

		return null;
	}
```
- example usage
```shell
...
synopsis
--------

'''javascript
var geoip = require('geoip-lite');

var ip = "207.97.227.239";
var geo = geoip.lookup(ip);

console.log(geo);
{ range: [ 3479297920, 3479301339 ],
country: 'US',
region: 'TX',
city: 'San Antonio',
ll: [ 29.4889, -98.3987 ],
...
```

#### <a name="apidoc.element.geoip-lite.pretty"></a>[function <span class="apidocSignatureSpan">geoip-lite.</span>pretty (n)](#apidoc.element.geoip-lite.pretty)
- description and source-code
```javascript
pretty = function (n) {
		if (typeof n === 'string') {
			return n;
		} else if (typeof n === 'number') {
			return utils.ntoa4(n);
		} else if (n instanceof Array) {
			return utils.ntoa6(n);
		}

		return n;
	}
```
- example usage
```shell
...
   ll: [<latitude>, <longitude>], // The latitude and longitude of the city
   metro: <metro code>,           // Metro code
   zip: <postal code>             // Postal code (IPv4 only)
}
'''

The actual values for the 'range' array depend on whether the IP is IPv4 or IPv6 and should be
considered internal to 'geoip-lite'.  To get a human readable format, pass them to 'geoip.pretty()'

If the IP address was not found, the 'lookup' returns 'null'

### Pretty printing an IP address ###

If you have a 32 bit unsigned integer, or a number returned as part of the 'range' array from the 'lookup' method,
the 'pretty' method can be used to turn it into a human readable string.
...
```

#### <a name="apidoc.element.geoip-lite.startWatchingDataUpdate"></a>[function <span class="apidocSignatureSpan">geoip-lite.</span>startWatchingDataUpdate (callback)](#apidoc.element.geoip-lite.startWatchingDataUpdate)
- description and source-code
```javascript
startWatchingDataUpdate = function (callback) {
		fsWatcher.makeFsWatchFilter(watcherName, geodatadir, 60*1000, function () {
			//Reload data
			async.series([
				function (cb) {
					preload(cb);
				},
				function (cb) {
					preload6(cb);
				}
			], callback);
		});
	}
```
- example usage
```shell
...

### Start and stop watching for data updates ###

If you have a server running 'geoip-lite', and you want to update its geo data without a restart, you can enable
the data watcher to automatically refresh in-memory geo data when a file changes in the data directory.

'''javascript
geoip.startWatchingDataUpdate();
'''

This tool can be used with 'npm run-script updatedb' to periodically update geo data on a running server.


Built-in Updater
----------------
...
```

#### <a name="apidoc.element.geoip-lite.stopWatchingDataUpdate"></a>[function <span class="apidocSignatureSpan">geoip-lite.</span>stopWatchingDataUpdate ()](#apidoc.element.geoip-lite.stopWatchingDataUpdate)
- description and source-code
```javascript
stopWatchingDataUpdate = function () {
		fsWatcher.stopWatching(watcherName);
	}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.geoip-lite.fsWatcher"></a>[module geoip-lite.fsWatcher](#apidoc.module.geoip-lite.fsWatcher)

#### <a name="apidoc.element.geoip-lite.fsWatcher.makeFsWatchFilter"></a>[function <span class="apidocSignatureSpan">geoip-lite.fsWatcher.</span>makeFsWatchFilter (name, directory, filename, cooldownDelay, callback)](#apidoc.element.geoip-lite.fsWatcher.makeFsWatchFilter)
- description and source-code
```javascript
function makeFsWatchFilter(name, directory, filename, cooldownDelay, callback) {
	var cooldownId = null;

	//Delete the cooldownId and callback the outer function
	function timeoutCallback() {
		cooldownId = null;
		callback();
	}

	//This function is called when there is a change in the data directory
	//It sets a timer to wait for the change to be completed
	function onWatchEvent(event, changedFile) {
		var filePath = path.join(directory, changedFile);

		if (!filename || filename === changedFile) {
			fs.exists(filePath, function onExists(exists) {
				if (!exists) {
					// if the changed file no longer exists, it was a deletion.
					// we ignore deleted files
					return;
				}

				//At this point, a new file system activity has been detected,
				//We have to wait for file transfert to be finished before moving on.

				//If a cooldownId already exists, we delete it
				if (cooldownId !== null) {
					clearTimeout(cooldownId);
					cooldownId = null;
				}

				//Once the cooldownDelay has passed, the timeoutCallback function will be called
				cooldownId = setTimeout(timeoutCallback, cooldownDelay);
			});
		}
	}

	//Manage the case where filename is missing (because it's optionnal)
	if (typeof cooldownDelay === 'function') {
		callback = cooldownDelay;
		cooldownDelay = filename;
		filename = null;
	}

	if (FSWatcher[name]) {
		stopWatching(name);
	}

	FSWatcher[name] = fs.watch(directory, onWatchEvent);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.geoip-lite.fsWatcher.stopWatching"></a>[function <span class="apidocSignatureSpan">geoip-lite.fsWatcher.</span>stopWatching (name)](#apidoc.element.geoip-lite.fsWatcher.stopWatching)
- description and source-code
```javascript
function stopWatching(name) {
	FSWatcher[name].close();
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
