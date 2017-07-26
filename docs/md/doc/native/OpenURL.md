# OpenURL

使用 OpenURL 打开某个应用，或者让应用决定应该如何响应 URL。

安卓也可以使用该 API，SDK 会调用系统浏览器，打开该 URL，具体该URL由什么应用处理，则交由 OS 控制。

## RequestParams
```
String URL;
```
## ResponseParams

-

## Example

例如，我需要打开微信应用，那么，应该调用 `wechat://`

```javascript
JSMessage.newMessage("Native.OpenURL", {
	URL: "wechat://"
}).call(null)
```

# CanOpenURL

使用 CanOpenURL 判断是否可以打开某个应用

一个应用是否可以打开，取决于两点

* 当前应用是否已经将目标应用添加到白名单（Info.plist）

* 目标应用是否已经安装

CanOpenURL 可以针对以上两点进行检测

## RequestParams
```
String URL;
```
## ResponseParams

-

## Example

例如，需要打开微信应用，那么，应该检测 `wechat://`

```javascript
JSMessage.newMessage("Native.CanOpenURL", {
	URL: "wechat://"
}).call(function(meta, result){
	if (meta.error){
		document.write("Can't Open"); 
		return console.error(error); 
	}
	else {
		document.write("Can Open");
	}
});
```