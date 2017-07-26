# FileManager

使用 FileManager 操控沙箱中的任意文件

你可以操控 Document / Caches / Tmp 目录中的任何文件，不受任何限制，但请注意以下要点。

* Document 该目录只能存放由用户主动生成的数据，不能存放缓存数据
* Caches 该目录存放缓存数据
* Tmp 该目录下的文件，会随时被清除

模块提供四个操作方法，写入、读取、检查、删除。

* read = 读取文件
* update = 写入文件
* delete = 删除文件
* check = 检查文件是否存在

## RequestParams
```
SUITE	 	suite;
OPT 		opt;
String 		filePath;
(String or Base64_String) fileContents;

enum SUITE {
	case "Document"
	case "Caches"
	case "Tmp"
}

enum OPT {
	case "read"
	case "update"
	case "delete"
	case "check"
}
```
## ResponseParams
```
(String or Base64_String) fileContents;
```
## Example

### 写入一个文件

```javascript
JSMessage.newMessage("Native.FileManager", {suite: "Caches", opt: "update", filePath: "test.txt", fileContents: "hello world"}).call(null);
```

### 读取一个文件

```javascript
JSMessage.newMessage("Native.FileManager", {suite: "Caches", opt: "read", filePath: "test.txt"}).call(function(meta, result){
	if (meta.error){ return console.error(error) }
	console.log(result.optSucceed, result.fileContents)
})
```
