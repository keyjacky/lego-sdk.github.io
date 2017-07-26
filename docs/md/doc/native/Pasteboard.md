# Pasteboard

使用 Pasteboard 模块可以将文本内容暂存到系统剪贴板中，在需要的时候，用户可以粘贴该内容。

## RequestParams
```
OPT    opt;
String string;

enum OPT {
	case "read"
	case "update"
	case "delete"
}
```
## ResponseParams
```
String string;
```
## Example

### update

```javascript
JSMessage.newMessage("Native.Pasteboard", {
	opt: "update",
	string: "罗老板，还是你！"
}).call(null)
```

### read

```javascript
JSMessage.newMessage("Native.Pasteboard", {
	opt: "read"
}).call(function(meta, result){
	if (meta.error){ return console.error(error); }
	console.log(result.string)
});
```

### delete

```javascript
JSMessage.newMessage("Native.Pasteboard", {
	opt: "delete"
}).call(null)
```