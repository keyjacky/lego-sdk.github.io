# DataModel

DataModel是原生应用与WebView进行数据交换的桥梁。

* 原生应用可以通过 DataModel 模块，向 WebView 传递数据。
* WebView 也可以通过 DataModel 模块，向 原生应用 传递数据。

## RequestParams
```
OPT     opt;
String  dataKey;
Any     dataValue;

enum OPT {
    case "update"
    case "read"
}
```
## ResponseParams

Whole dataModel maps;

## Example

### 初始化数据

WebView 在加载完成时，应该请求一次 DataModel 全量数据，以获取在网页未加载完成时的暂存数据。并把 `JSDataModel` 变量挂在window对象下, 否则数据变化触发的 `JSDataModelDidChanged` 方法会不生效

```javascript
window.JSDataModel = {}
function init() {
    JSMessage.newMessage("Native.DataModel").call(function(dataModel){
        window.JSDataModel = dataModel
        console.log(dataModel)
    })
}
```

### 传递数据

原生应用使用以下方法，向 WebView 传递数据。

```swift
self.webView.updateDataModel("date", dataValue: NSDate().description)
```

WebView 使用以下方法，向原生应用传递数据。

```javascript
JSMessage.newMessage("Native.DataModel", {
    opt: "update",
    dataKey: "word",
    dataValue: "Hello, World!"
}).call(null);
```

### 响应数据变化

DataModel 中的数据变化时，JSDataModelDidChanged 函数会被调用，你可以通过定义该函数，响应数据变化。

```javascript
window.JSDataModelDidChanged(dataKey) {
    if (dataKey == "date") {
        // do something
    }
}
```