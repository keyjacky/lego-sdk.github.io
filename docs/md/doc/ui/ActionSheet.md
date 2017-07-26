# ActionSheet

使用 ActionSheet 可以弹出一个包含多个选项的对话框，用户选择对应选项后会有回调。点击取消选项和点击蒙版区域触发相同的事件。

## RequestParams
```
String   title;
String[] buttonTitles;
Int      dangerButton;
String   cancelButton;
```
## ResponseParams
```
Int buttonIndex; 
```
## Example

```javascript
JSMessage.newMessage("UI.ActionSheet", {
    title: "请问，罗老板隐婚了多久？",
    buttonTitles: ["一年", "两年", "三年", "五年"],
    dangerButton: 3,
    cancelButton: "我选择死亡"
}).call(function(meta, result) {
	if (meta.error){ return console.error(error); }
	console.log(result.buttonIndex)
})
```




