# Check

使用 Check API 检查当前SDK版本以及当前SDK可用的模块。

支持同步的方式获取返回结果。

## RequestParams

-

## ResponseParams
```
String SDKVersion;
RESULT checkResult;

RESULT {
	(String)moduleName: (Int)moduleVersion;
}
```
## Example

```
// 同步调用
var syncResult = JSMessage.newMessage("Native.Check").call()
console.log(syncResult)

// 异步调用
JSMessage.newMessage("Native.Check").call(function(meta, result) {
	if (meta.error){ return console.error(error); }
	console.log(result.checkResult['Native.Check'])
})
```
