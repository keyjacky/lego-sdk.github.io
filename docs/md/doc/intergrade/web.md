# Web

当 Native 端完成相应模块集成后，在 Web 端就可以发起 SDK 请求了。

## 初始化

发起请求前，需要先执行初始化代码，以初始化 SDK 环境。

```js
window.JSBridge && eval(window.JSBridge.bridgeScript())
```

## 发起异步请求

```
JSMessage.newMessage('Native.Device', {aKey: "aValue"}).call(
    function(meta, res){
        document.write('Device Name = ' + res.device.name)
    }
);
```

其中，第一个参数是模块名称，第二个参数是请求内容，使用 call 方法，发起请求。

当请求完成或失败时，call 回调会被执行。

回调的第一个参数是 meta ，第二个参数则是 response 对象。其中 meta 对象包含一些错误或成功的状态信息。如果 meta.error === true，则存在错误。

## 发起同步请求

部分 API 是支持同步返回结果的，比如 Native.Device 和 Native.Check，使用以下方法，获取同步结果。

```
var res = JSMessage.newMessage('Native.Device', {aKey: "aValue"}).call();
document.write('Device Name = ' + res.device.name);
```

