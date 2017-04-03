# api documentation for  [local-web-server (v1.2.7)](https://github.com/75lb/local-web-server#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-local-web-server.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-local-web-server) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-local-web-server.svg)](https://travis-ci.org/npmdoc/node-npmdoc-local-web-server)
#### A simple web-server for productive front-end development

[![NPM](https://nodei.co/npm/local-web-server.png?downloads=true)](https://www.npmjs.com/package/local-web-server)

[![apidoc](https://npmdoc.github.io/node-npmdoc-local-web-server/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-local-web-server_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-local-web-server/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-local-web-server/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-local-web-server/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Lloyd Brookes",
        "email": "75pound@gmail.com"
    },
    "bin": {
        "ws": "./bin/cli.js"
    },
    "bugs": {
        "url": "https://github.com/75lb/local-web-server/issues"
    },
    "dependencies": {
        "ansi-escape-sequences": "^3.0.0",
        "array-back": "^1.0.4",
        "command-line-args": "^4.0.2",
        "command-line-usage": "^4.0.0",
        "config-master": "^3.0.0",
        "debug": "^2.2.0",
        "http-proxy": "^1.15.1",
        "kcors": "^1.3.0",
        "koa": "2.0.1",
        "koa-bodyparser": "^3.0.0",
        "koa-compress": "^1.0.9",
        "koa-conditional-get": "^1.0.3",
        "koa-connect-history-api-fallback": "^0.3.1",
        "koa-convert": "^1.2.0",
        "koa-etag": "^2.1.1",
        "koa-json": "^1.1.3",
        "koa-morgan": "^1.0.1",
        "koa-rewrite": "^2.1.0",
        "koa-route": "^3",
        "koa-send": "^3.2.0",
        "koa-serve-index": "^1.1.1",
        "koa-static": "^2.0.0",
        "path-to-regexp": "^1.6.0",
        "reduce-flatten": "^1.0.1",
        "stream-log-stats": "^1.1.7",
        "test-value": "^2.1.0",
        "typical": "^2.6.0"
    },
    "description": "A simple web-server for productive front-end development",
    "devDependencies": {
        "jsdoc-to-markdown": "^3.0.0",
        "req-then": "^0.2.4",
        "tape": "^4.6.2"
    },
    "directories": {},
    "dist": {
        "shasum": "c3b5079cc07059bd5efce369f16b1802d44a1929",
        "tarball": "https://registry.npmjs.org/local-web-server/-/local-web-server-1.2.7.tgz"
    },
    "engines": {
        "node": ">=4.0.0"
    },
    "gitHead": "185845c63017f2ddcce8911eeaa7b7366ed79a7e",
    "homepage": "https://github.com/75lb/local-web-server#readme",
    "keywords": [
        "dev",
        "server",
        "web",
        "tool",
        "front-end",
        "development",
        "cors",
        "mime",
        "rest"
    ],
    "license": "MIT",
    "main": "lib/local-web-server.js",
    "maintainers": [
        {
            "name": "75lb",
            "email": "lloyd.brookes@gmail.com"
        }
    ],
    "name": "local-web-server",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/75lb/local-web-server.git"
    },
    "scripts": {
        "cover": "istanbul cover ./node_modules/.bin/tape test/*.js && cat coverage/lcov.info | coveralls && rm -rf coverage; echo",
        "docs": "jsdoc2md -t jsdoc2md/README.hbs -p list lib/*.js > README.md; echo",
        "test": "tape test/*.js"
    },
    "version": "1.2.7"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module local-web-server](#apidoc.module.local-web-server)
1.  object <span class="apidocSignatureSpan">local-web-server.</span>middleware

#### [module local-web-server.middleware](#apidoc.module.local-web-server.middleware)
1.  [function <span class="apidocSignatureSpan">local-web-server.middleware.</span>blacklist (forbid)](#apidoc.element.local-web-server.middleware.blacklist)
1.  [function <span class="apidocSignatureSpan">local-web-server.middleware.</span>mime (mimeTypes)](#apidoc.element.local-web-server.middleware.mime)
1.  [function <span class="apidocSignatureSpan">local-web-server.middleware.</span>mockResponses (route, targets)](#apidoc.element.local-web-server.middleware.mockResponses)
1.  [function <span class="apidocSignatureSpan">local-web-server.middleware.</span>proxyRequest (route)](#apidoc.element.local-web-server.middleware.proxyRequest)



# <a name="apidoc.module.local-web-server"></a>[module local-web-server](#apidoc.module.local-web-server)



# <a name="apidoc.module.local-web-server.middleware"></a>[module local-web-server.middleware](#apidoc.module.local-web-server.middleware)

#### <a name="apidoc.element.local-web-server.middleware.blacklist"></a>[function <span class="apidocSignatureSpan">local-web-server.middleware.</span>blacklist (forbid)](#apidoc.element.local-web-server.middleware.blacklist)
- description and source-code
```javascript
function blacklist(forbid) {
  return function blacklist (ctx, next) {
    if (forbid.some(expression => pathToRegexp(expression).test(ctx.path))) {
      ctx.throw(403, http.STATUS_CODES[403])
    } else {
      return next()
    }
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.local-web-server.middleware.mime"></a>[function <span class="apidocSignatureSpan">local-web-server.middleware.</span>mime (mimeTypes)](#apidoc.element.local-web-server.middleware.mime)
- description and source-code
```javascript
function mime(mimeTypes) {
  return function mime (ctx, next) {
    return next().then(() => {
      const reqPathExtension = path.extname(ctx.path).slice(1)
      Object.keys(mimeTypes).forEach(mimeType => {
        const extsToOverride = mimeTypes[mimeType]
        if (extsToOverride.indexOf(reqPathExtension) > -1) ctx.type = mimeType
      })
    })
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.local-web-server.middleware.mockResponses"></a>[function <span class="apidocSignatureSpan">local-web-server.middleware.</span>mockResponses (route, targets)](#apidoc.element.local-web-server.middleware.mockResponses)
- description and source-code
```javascript
function mockResponses(route, targets) {
  targets = arrayify(targets)
  debug('mock route: %s, targets: %s', route, targets.length)
  const pathRe = pathToRegexp(route)

  return function mockResponse (ctx, next) {
    if (pathRe.test(ctx.path)) {
      const testValue = require('test-value')

<span class="apidocCodeCommentSpan">      /* find a mock with compatible method and accepts */
</span>      let target = targets.find(target => {
        return testValue(target, {
          request: {
            method: [ ctx.method, undefined ],
            accepts: type => ctx.accepts(type)
          }
        })
      })

      /* else take the first target without a request (no request means 'all requests') */
      if (!target) {
        target = targets.find(target => !target.request)
      }

      if (target) {
        if (t.isFunction(target.response)) {
          const pathMatches = ctx.path.match(pathRe).slice(1)
          return target.response.apply(null, [ctx].concat(pathMatches))
        } else if (t.isPlainObject(target.response)) {
          Object.assign(ctx.response, target.response)
        } else {
          throw new Error('Invalid response: ${JSON.stringify(target.response)}')
        }
      }
    } else {
      return next()
    }
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.local-web-server.middleware.proxyRequest"></a>[function <span class="apidocSignatureSpan">local-web-server.middleware.</span>proxyRequest (route)](#apidoc.element.local-web-server.middleware.proxyRequest)
- description and source-code
```javascript
function proxyRequest(route) {
  const httpProxy = require('http-proxy')
  const proxy = httpProxy.createProxyServer({
    changeOrigin: true,
    secure: false
  })
  proxy.on('error', err => {
    // not worth crashing for
  })

  return function proxyMiddleware () {
    const keys = []
    route.re = pathToRegexp(route.from, keys)
    route.new = this.url.replace(route.re, route.to)

    keys.forEach((key, index) => {
      const re = RegExp(':${key.name}', 'g')
      route.new = route.new
        .replace(re, arguments[index + 1] || '')
    })

    debug('proxy request', 'from: ${this.path}, to: ${url.parse(route.new).href}')

    return new Promise((resolve, reject) => {
      proxy.once('error', err => {
        err.message = '[PROXY] Error: ${err.message} Target: ${route.new}'
        reject(err)
      })
      proxy.once('proxyReq', function (proxyReq) {
        proxyReq.path = url.parse(route.new).path
      })
      proxy.once('close', resolve)
      proxy.web(this.req, this.res, { target: route.new })
    })
  }
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
