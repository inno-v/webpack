
# example.js

``` javascript
var Worker = require("worker!./worker");
var worker = new Worker;
worker.postMessage("b");
worker.onmessage = function(event) {
	var templateB = event.data; // "This text was generated by template B"
}
```

# worker.js

``` javascript
onmessage = function(event) {
	var template = event.data;
	require(["../require.context/templates/" + event.data], function(tmpl) {
		postMessage(tmpl());
	});
}

```

# js/output.js

``` javascript
/******/ (function(modules) { // webpackBootstrap
/******/ 	
/******/ 	// The module cache
/******/ 	var installedModules = {};
/******/ 	
/******/ 	// The require function
/******/ 	function __webpack_require__(moduleId) {
/******/ 		// Check if module is in cache
/******/ 		if(installedModules[moduleId])
/******/ 			return installedModules[moduleId].exports;
/******/ 		
/******/ 		// Create a new module (and put it into the cache)
/******/ 		var module = installedModules[moduleId] = {
/******/ 			exports: {},
/******/ 			id: moduleId,
/******/ 			loaded: false
/******/ 		};
/******/ 		
/******/ 		// Execute the module function
/******/ 		modules[moduleId].call(module.exports, module, module.exports, __webpack_require__);
/******/ 		
/******/ 		// Flag the module as loaded
/******/ 		module.loaded = true;
/******/ 		
/******/ 		// Return the exports of the module
/******/ 		return module.exports;
/******/ 	}
/******/ 	
/******/ 	
/******/ 	// expose the modules object (__webpack_modules__)
/******/ 	__webpack_require__.m = modules;
/******/ 	
/******/ 	// expose the module cache
/******/ 	__webpack_require__.c = installedModules;
/******/ 	
/******/ 	// __webpack_public_path__
/******/ 	__webpack_require__.p = "js/";
/******/ 	
/******/ 	
/******/ 	// Load entry module and return exports
/******/ 	return __webpack_require__(0);
/******/ })
/************************************************************************/
/******/ ([
/* 0 */
/*!********************!*\
  !*** ./example.js ***!
  \********************/
/***/ function(module, exports, __webpack_require__) {

	var Worker = __webpack_require__(/*! worker!./worker */ 1);
	var worker = new Worker;
	worker.postMessage("b");
	worker.onmessage = function(event) {
		var templateB = event.data; // "This text was generated by template B"
	}

/***/ },
/* 1 */
/*!*********************************************!*\
  !*** (webpack)/~/worker-loader!./worker.js ***!
  \*********************************************/
/***/ function(module, exports, __webpack_require__) {

	module.exports = function() {
		return new Worker(__webpack_require__.p + "hash.worker.js");
	};

/***/ }
/******/ ])
```

# js/[hash].worker.js

``` javascript
/******/ (function(modules) { // webpackBootstrap
/******/ 	
/******/ 	// The module cache
/******/ 	var installedModules = {};
/******/ 	
/******/ 	// object to store loaded chunks
/******/ 	// "1" means "already loaded"
/******/ 	var installedChunks = {
/******/ 		1:1
/******/ 	};
/******/ 	
/******/ 	// The require function
/******/ 	function __webpack_require__(moduleId) {
/******/ 		// Check if module is in cache
/******/ 		if(installedModules[moduleId])
/******/ 			return installedModules[moduleId].exports;
/******/ 		
/******/ 		// Create a new module (and put it into the cache)
/******/ 		var module = installedModules[moduleId] = {
/******/ 			exports: {},
/******/ 			id: moduleId,
/******/ 			loaded: false
/******/ 		};
/******/ 		
/******/ 		// Execute the module function
/******/ 		modules[moduleId].call(module.exports, module, module.exports, __webpack_require__);
/******/ 		
/******/ 		// Flag the module as loaded
/******/ 		module.loaded = true;
/******/ 		
/******/ 		// Return the exports of the module
/******/ 		return module.exports;
/******/ 	}
/******/ 	
/******/ 	// This file contains only the entry chunk.
/******/ 	// The chunk loading function for additional chunks
/******/ 	__webpack_require__.e = function requireEnsure(chunkId, callback) {
/******/ 		// "1" is the signal for "already loaded"
/******/ 		if(!installedChunks[chunkId]) {
/******/ 			importScripts("" + chunkId + ".hash.worker.js");
/******/ 		}
/******/ 		callback.call(null, __webpack_require__);
/******/ 	};
/******/ 	
/******/ 	// expose the modules object (__webpack_modules__)
/******/ 	__webpack_require__.m = modules;
/******/ 	
/******/ 	// expose the module cache
/******/ 	__webpack_require__.c = installedModules;
/******/ 	
/******/ 	// __webpack_public_path__
/******/ 	__webpack_require__.p = "";
/******/ 	this["webpackChunk"] = function webpackChunkCallback(chunkIds, moreModules) {
/******/ 		for(var moduleId in moreModules) {
/******/ 			modules[moduleId] = moreModules[moduleId];
/******/ 		}
/******/ 		while(chunkIds.length)
/******/ 			installedChunks[chunkIds.pop()] = 1;
/******/ 	};
/******/ 	
/******/ 	// Load entry module and return exports
/******/ 	return __webpack_require__(0);
/******/ })
/************************************************************************/
/******/ ([
/* 0 */
/*!*******************!*\
  !*** ./worker.js ***!
  \*******************/
/***/ function(module, exports, __webpack_require__) {

	onmessage = function(event) {
		var template = event.data;
		__webpack_require__.e/* require */(0, function(__webpack_require__) { var __WEBPACK_AMD_REQUIRE_ARRAY__ = [__webpack_require__(/*! ../require.context/templates */ 4)("./" + event.data)]; (function(tmpl) {
			postMessage(tmpl());
		}.apply(null, __WEBPACK_AMD_REQUIRE_ARRAY__));});
	}


/***/ }
/******/ ])
```

# js/0.[hash].worker.hs

``` javascript
webpackChunk([0],[
/* 0 */,
/* 1 */
/*!*****************************************!*\
  !*** ../require.context/templates/a.js ***!
  \*****************************************/
/***/ function(module, exports, __webpack_require__) {

	module.exports = function() {
		return "This text was generated by template A";
	}

/***/ },
/* 2 */
/*!*****************************************!*\
  !*** ../require.context/templates/b.js ***!
  \*****************************************/
/***/ function(module, exports, __webpack_require__) {

	module.exports = function() {
		return "This text was generated by template B";
	}

/***/ },
/* 3 */
/*!*****************************************!*\
  !*** ../require.context/templates/c.js ***!
  \*****************************************/
/***/ function(module, exports, __webpack_require__) {

	module.exports = function() {
		return "This text was generated by template C";
	}

/***/ },
/* 4 */
/*!*********************************************!*\
  !*** ../require.context/templates ^\.\/.*$ ***!
  \*********************************************/
/***/ function(module, exports, __webpack_require__) {

	var map = {
		"./a": 1,
		"./a.js": 1,
		"./b": 2,
		"./b.js": 2,
		"./c": 3,
		"./c.js": 3
	};
	function webpackContext(req) {
		return __webpack_require__(webpackContextResolve(req));
	};
	function webpackContextResolve(req) {
		return map[req] || (function() { throw new Error("Cannot find module '" + req + "'.") }());
	};
	webpackContext.keys = function webpackContextKeys() {
		return Object.keys(map);
	};
	webpackContext.resolve = webpackContextResolve;
	module.exports = webpackContext;


/***/ }
])
```

# Info

## Uncompressed

```
Hash: d3a484ec9964172dc379
Version: webpack 1.1.0
Time: 108ms
           Asset  Size  Chunks             Chunk Names
0.hash.worker.js  1653          [emitted]             
  hash.worker.js  2831          [emitted]             
       output.js  2167       0  [emitted]  main       
chunk    {0} output.js (main) 302 [rendered]
    > main [0] ./example.js 
    [0] ./example.js 206 {0} [built]
    [1] (webpack)/~/worker-loader!./worker.js 96 {0} [not cacheable] [built]
        cjs require worker!./worker [0] ./example.js 1:13-39
Child worker:
    Hash: 374188a31a72007585d1
    Version: webpack 1.1.0
               Asset  Size  Chunks             Chunk Names
    0.hash.worker.js  1653       0  [emitted]             
      hash.worker.js  2831       1  [emitted]  main       
    chunk    {0} 0.hash.worker.js 463 {1} [rendered]
        > [0] ./worker.js 3:1-5:3
        [1] ../require.context/templates/a.js 82 {0} [built]
            context element ./a.js [4] ../require.context/templates ^\.\/.*$
            context element ./a [4] ../require.context/templates ^\.\/.*$
        [2] ../require.context/templates/b.js 82 {0} [built]
            context element ./b.js [4] ../require.context/templates ^\.\/.*$
            context element ./b [4] ../require.context/templates ^\.\/.*$
        [3] ../require.context/templates/c.js 82 {0} [built]
            context element ./c.js [4] ../require.context/templates ^\.\/.*$
            context element ./c [4] ../require.context/templates ^\.\/.*$
        [4] ../require.context/templates ^\.\/.*$ 217 {0} [built]
            amd require context ../require.context/templates [0] ./worker.js 3:1-5:3
    chunk    {1} hash.worker.js (main) 168 [rendered]
        > main [0] ./worker.js 
        [0] ./worker.js 168 {1} [built]
```

## Minimized (uglify-js, no zip)

```
Hash: e028e5c3f2a9ee017ccf
Version: webpack 1.1.0
Time: 235ms
           Asset  Size  Chunks             Chunk Names
0.hash.worker.js   528          [emitted]             
  hash.worker.js   513          [emitted]             
       output.js   371       0  [emitted]  main       
chunk    {0} output.js (main) 302 [rendered]
    > main [0] ./example.js 
    [0] ./example.js 206 {0} [built]
    [1] (webpack)/~/worker-loader!./worker.js 96 {0} [not cacheable] [built]
        cjs require worker!./worker [0] ./example.js 1:13-39

WARNING in output.js from UglifyJs
Side effects in initialization of unused variable templateB [./example.js:5,0]
Child worker:
    Hash: f557b852479205b3c82c
    Version: webpack 1.1.0
               Asset  Size  Chunks             Chunk Names
    0.hash.worker.js   528       0  [emitted]             
      hash.worker.js   513       1  [emitted]  main       
    chunk    {0} 0.hash.worker.js 463 {1} [rendered]
        > [0] ./worker.js 3:1-5:3
        [1] ../require.context/templates/a.js 82 {0} [built]
            context element ./a.js [4] ../require.context/templates ^\.\/.*$
            context element ./a [4] ../require.context/templates ^\.\/.*$
        [2] ../require.context/templates/b.js 82 {0} [built]
            context element ./b.js [4] ../require.context/templates ^\.\/.*$
            context element ./b [4] ../require.context/templates ^\.\/.*$
        [3] ../require.context/templates/c.js 82 {0} [built]
            context element ./c.js [4] ../require.context/templates ^\.\/.*$
            context element ./c [4] ../require.context/templates ^\.\/.*$
        [4] ../require.context/templates ^\.\/.*$ 217 {0} [built]
            amd require context ../require.context/templates [0] ./worker.js 3:1-5:3
    chunk    {1} hash.worker.js (main) 168 [rendered]
        > main [0] ./worker.js 
        [0] ./worker.js 168 {1} [built]
    
    WARNING in hash.worker.js from UglifyJs
    Side effects in initialization of unused variable template [./worker.js:2,0]
```