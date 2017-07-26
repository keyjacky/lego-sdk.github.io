# PageState

使用 PageState 模块可以获取当前页面、应用的工作状态。

## RequestParams

-

## ResponseParams

```

/**
 * "appear"     - 当前页面正在显示
 * "disappear"  - 当前页面被隐藏
 * "active"     - 当前应用正在活动 
 * "inactive"   - 当前应用正在后台
 */
string currentState;

```

## Example

```javascript
JSMessage.newMessage("UI.PageState").call(function(meta, result){
    console.log(result.currentState);
});
```

