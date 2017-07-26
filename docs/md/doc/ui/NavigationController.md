# NavigationController

使用 NavigationController 模块，你可以将应用跳转至下一个页面，也可以返回至上一个页面。

提供 path 参数，并为其提供一个URL，即可跳转至下一页。

提供 args 参数，并为其提供一些下一页面所需要的变量，下一页面可以通过 window._args 访问到。

## RequestParams
```
OPT     opt;
String  path;
Bool    animated;
Object  args;

enum OPT {
    case "push"
    case "pop"
}

```
## ResponseParams

-

## Example

```javascript
// #1 假设，要将 https://www.google.com.hk/ 作为下一页面进行跳转。
JSMessage.newMessage("UI.NavigationController", {
    opt: "push",
    path: "https://www.google.com.hk/",
    args: {
        customID: 8888,
    }
}).call(null)

// #2 在必要的时候，使用以下方法退出本页面。
JSMessage.newMessage("UI.NavigationController", {
    opt: "pop"
}).call(null)
```