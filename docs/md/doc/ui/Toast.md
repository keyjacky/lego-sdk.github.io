# Toast

使用 Toast 模块可以显示一个原生的 Loading 指示器，在指示器工作期间，界面将暂停响应（阻塞）。

## RequestParams

```

string opt;     // 动作，>>> 'show', 'hide'
string style;   // 图标样式，>>> 'loading', 'success', 'error', 'text'
string title;   // 图标下方的提示文字
int    timeout; // 超时值，仅对于 style === "loading" 时有效，最大值为 10，当超过 timeout 时，Toast 会被隐藏。
bool   masked;  // 遮罩，为true时遮罩生效，false则不生效
```

## ResponseParams

-

## Example

```javascript
JSMessage.newMessage("UI.Toast", {
    opt: "show",
    style: "loading",
    title: "加载中",
    timeout: 10,
    masked: true,
}).call(null);
```
