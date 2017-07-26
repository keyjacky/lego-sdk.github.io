# HTTPRequest

使用 HTTPRequest 模块可以突破跨域限制，无须JSONP，直接获取任意HTTP数据。

如果HTTP数据是 UTF-8 字符串，则直接返回 responseText，否则，返回 Base64 编码后的 String 至 responseData。

你还可以添加自定义的 HTTP Header 到请求的头部。

## 安全

如果使用该 API，Native 会禁用任何自带的 Cookie 信息，以保证安全性。如果需要使用 Cookie，你需要自行将其添加至 Header 中，或者使用Web提供的Ajax方法。

## RequestParams
```
String 			URL;
Base64_String 	data;
Bool 			showActivityIndicator;
Int				timeout;
Object 			headers; 
```
## ResponseParams
```
Int 			statusCode;
String 			responseText;
Base64_String 	responseData;
```
## Example

```javascript
// 获取一个GitHub的接口数据
JSMessage.newMessage("Native.HTTPRequest", {
	URL: "https://status.github.com/api.json",
	headers: {aKey: "aValue"}
}).call(function(meta, result) {
	if (meta.error){ return console.error(error); }
	console.log(result)
})

// 获取图片数据
JSMessage.newMessage("Native.HTTPRequest", {
	URL: "http://www.huanju.cn/s/v1206/HuanJu-LOGO-PNG.png"
}).call(function(meta, result){
	if (meta.error){ return console.error(error); }
})
```