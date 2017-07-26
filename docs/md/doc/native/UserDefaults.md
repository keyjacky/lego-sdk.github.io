# UserDefaults

UserDefaults 模块可以保存一些简单的数据，并持久化到闪存中。

UserDefaults 和 Cookie 比较类似，不同的是， UserDefaults 并不会默认传输到网站， UserDefaults 相当于一个简单的 Key-Value 数据库。

UserDefaults 可以创建多个仓库，不同仓库有不同的 Key-Value 数据。

## RequestParams
```
OPT		opt;
String 	suite;
String 	key;
Any 	value;

enum OPT {
	case "create"
	case "update"
	case "read"
	case "delete"
}
```

* 当 suite 以 memory:// 开头时，数据将被保存至内存，应用退出后，数据会被清除。
* 当 suite 以 cache:// 开头时，数据在被保存至内存的同时，当应用内存不足时，数据会被随机清除。

## ResponseParams
```
Any value;
```
## Example

### 保存一对 Key-Value 到仓库

```javascript
JSMessage.newMessage("Native.UserDefaults", {
	opt: "update",
	key: "test",
	value: "hello"
}).call(null)
```

### 读取一对 Key-Value

```javascript
JSMessage.newMessage("Native.UserDefaults", {
	opt: "read",
	key: "test"
}).call(function(meta, result){
	if (meta.error){ return console.error(error); }
	console.log(result.value)
})
```