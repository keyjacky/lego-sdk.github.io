# NavigationItem

使用 NavigationItem 模块可以自定义应用页面导航栏左侧按钮、右侧按钮以及页面标题。

也可以使用 NavigationItem 模块设置下一页面的返回按钮标题。

其中左侧按钮、右侧按钮可以设置为文本按钮或者图标按钮。

## RequestParams
```
String leftItem;
String rightItem;
```
## ResponseParams
```
Bool leftTapped;
Bool rightTapped;
```
## Example

```javascript

// 设置右侧按钮为图标按钮，那么，需要提供一个参数 rightItem，并为其提供图标地址或者文本。
JSMessage.newMessage("UI.NavigationItem", {
	rightItem: "https://raw.githubusercontent.com/Redtory/Product-Roadmap/master/barbuttonicon_addfriends%403x.png"
}).call(function(meta, result){
	if (meta.error){ return console.error(error); }
	if (result.rightTapped) {
        console.log("Done button tapped.")
    }
})

```