# OpenIntent

使用 OpenIntent 打开某个应用，或者让应用决定应该如何响应 URL。

需指定`目标应用的 Package 名称`，以及`目标应用的 Activity 名称`。

## RequestParams

String name;
String action;

## ResponseParams

-

## Example

例如，我需要打开微信应用，那么，应该这样调用

```javascript
JSMessage.newMessage("Native.OpenIntent", {
	name: "com.tencent.mm",
	action: "com.tencent.mm.ui.LauncherUI"
}).call(function(meta, result){
	if (meta.error){ return console.error(error); }
	document.write(result.succeed);
});
```

# CanOpenIntent

使用 CanOpenIntent 判断是否可以打开某个应用

需指定`目标应用的 Package 名称`，以及`目标应用的 Activity 名称`。

## RequestParams

String name;
String action;

## ResponseParams

-

## Example

```javascript
JSMessage.newMessage("Native.CanOpenIntent", {
	name: "com.tencent.mm",
	action: "com.tencent.mm.ui.LauncherUI"
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