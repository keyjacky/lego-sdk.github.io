# LEGO-SDK-JS

* 封装 `LEGO SDK` 的 `Native` 和 `UI` 系列模块；
* 针对以上模块，提供 `Promiseable` 的调用方式，处理异步和异常更简洁；
* 以及提供一个 `d.ts` 头文件，获得语法提示。

### 源码

提供以下两种获取方式：

* `npm` ，执行 `npm i lego-js-sdk` 拉取
* Duowan CDN
	* [lego-sdk.min.js][6]
	* [sdk_env.d.ts][7]




### 接入
在html页面引入:  `<script src="./node_modules/lego-sdk-js/dist/sdk.js" ></script>`

或者在`.js` `.ts`文件: `require("./node_modules/lego-sdk-js/dist/sdk.js")`


### 语法提示

满足2个条件就可获得 `LEGO-SDK-JS` 语法提示。

1. 让你的 IDE 支持 TypeScript  
	* Atom: 执行 `apm install atom-typescript`，然后重启。
	* Sumlime: 通过 `Package Control`安装 [`TypeScript-Sublime-Plugin`]
	* Webstorm / Eclipse / NetBeans [详情][1] 
2. 需要提示的 js文件头部引入 `d.ts` 文件，比如
```typescript
/// <reference path="./node_modules/lego-sdk-js/typings/es6/promise.d.ts" />
/// <reference path="./node_modules/lego-sdk-js/typings/sdk_env.d.ts" />
``` 

### 模块调用
参见文档

[1]: [https://github.com/Microsoft/TypeScript/wiki/TypeScript-Editor-Support]
[2]: [https://atom.io/packages/atom-typescript]
[3]: [https://github.com/Microsoft/TypeScript-Sublime-Plugin]
[4]: [https://github.com/LEGO-SDK/LEGO-SDK-JS/blob/master/typings/sdk_env.d.ts]
[5]: [https://github.com/LEGO-SDK/LEGO-SDK-JS]
[6]: [http://assets.dwstatic.com/project/lego-sdk/0.0.1/lego-sdk.min.js]
[7]: [http://assets.dwstatic.com/project/lego-sdk/0.0.1/typings/sdk_env.d.ts]