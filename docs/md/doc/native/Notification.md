# Notification

使用 Notification 可以跨 WebView 通讯，而 Notification 在 iOS 中实际上就是 NSNotification，在 Android 中实际上就是 Boardcast。

一个通知可以分为两个角色，发送者、观察者。

发送者，负责发送通知。

观察者，负责响应通知。

使用 Notification 模块除了可以响应通知以外，还可以接收到通知的额外信息。

使用 Notification 模块也可以发送通知信息。

## RequestParams
```
OPT    opt;
String name;
String aPostObject;
Object aPostUserInfo;

enum OPT {
	case "create"
	case "delete"
	case "post"
}
```
## ResponseParams
```
String object;
Object userInfo;
```
## Example

### 监听通知（添加观察者）

监听应用退出后台以后，重新进入的事件。

```javascript
JSMessage.newMessage("Native.Notification", {
    name: "UIApplicationDidBecomeActiveNotification"
}).call(function () {
    //应用重新进入后，该代码块被调用。
});
```

### 发送通知（通知观察者）

我们也可以主动发送一个通知

```javascript
JSMessage.newMessage("Native.Notification", {
	name: "Test",
	opt: "post",
	aPostObject: "This notification is post via WebView", 	aPostUserInfo: {aKey: "aValue"}
}).call(null);
```

### 移除观察者

如果不再需要监听相关事件，使用 delete 进行移除。
name 留空则表示，移除当前 web 页所有的监听者。
name 不留空则表示移除当前 web 页该 name  的所有监听者。

```javascript
JSMessage.newMessage("Native.Notification"{
	opt:"delete",
	name:""
}).call(null)
```