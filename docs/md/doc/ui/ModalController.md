# ModalController

ModalController 与 NavigationController 使用方法类似，但是，ModalController 跳转的页面，是以模态的形式呈现的。

默认的呈现动画是自下而上。

## RequestParams
```
OPT     opt;                    // 操作
String  path;                   // 路径（绝对或相对）
Bool    animated;               // 是否以动画形式呈现下一界面
Bool    clearWebView;           // 下一界面的 WebView 背景是否透明
Bool    clearMask;              // 下一界面的 MaskView 背景是否透明
Bool    nonMask;                // 下一界面的 MaskView 是否去掉
MType   modalType;              // Modal 的呈现模式
Float   modalWidth;             // Modal 的宽
Float   modalHeight;            // Modal 的高
Object  args;                   // 要向下一界面的 WebView 传递的参数
String  preloadToken;   // 针对 WebView.Preload API 使用

enum OPT {
    case "present"
    case "dismiss"
}

enum LGOModalType {
    Normal = 0,     // 模态窗口铺满全屏
    Center = 1,     // 模态窗口居中
    Top = 2,        // 居上
    Left = 3,       // 居左
    Bottom = 4,     // 居下
    Right = 5,      // 居右
};

```
## ResponseParams

-

## Example

```javascript
// #1 将 https://www.google.com.hk/ 作为模态页面弹入。
JSMessage.newMessage("UI.ModalController", {
    opt: "present",
    path: "https://www.google.com.hk/",
    args: {
        customID: 8888,
    }
}).call(null)

// #2 退出当前页面
JSMessage.newMessage("UI.ModalController", {
    opt: "dismiss"
}).call(null)
```