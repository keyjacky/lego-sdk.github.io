# AlertView

使用 AlertView 模块弹出一个原生的警告对话框，用户选择对应选项后会有回调。

## RequestParams
```
String      title;
String      message;
String[]    buttonTitles;
```
## ResponseParams
```
Int buttonIndex;
```
## Example

```javascript
JSMessage.newMessage("UI.AlertView", {
    title: "即将毁灭地球，请确认。",
    buttonTitles: ["马上毁灭", "稍后再试"]
}).call(function(meta, result) {
    console.log(result)
    if (result.buttonIndex == 0) {
        console.log("正在发射核弹...");
    }
    else {
        console.log("太迟了......");
    }
})
```
