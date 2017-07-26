# Call

使用 Call 模块， WebView 可以主动触发原生 ViewController 的 `call` 方法。

通过该模块，你可以实现当用户点按某个Web元素时，要求 ViewController 进行事件响应的需求。

## RequestParams
```
String methodName;
Object userInfo;
```
## ResponseParams

-

## Example

```javascript
JSMessage.newMessage("Native.Call", {
	methodName: "callMe",
	userInfo: {name: "Pony"}
}).call(null);
```