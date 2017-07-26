# Refresh

使用 Refresh 模块可以为 WebView 添加一个原生的下拉刷新控制器。

## RequestParams
```
OPT opt;

enum OPT {
    case "add"
    case "complete"
}
```
## ResponseParams

-

## Example

```javascript
JSMessage.newMessage("UI.Refresh", {
    opt: "create"
}).call(function nowRefresh(){
    // 调用此方法，结束刷新控制器的动画
    setTimeout(function(){
        message.requestParams = {
            opt: "complete"
        }
        message.call(null)
    }, 2000)
}.bind(this))
```
