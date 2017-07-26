# Page

可使用 Page API 为每一个 Web 页面定义『标题文本』、『状态栏样式』、『导航栏样式』等。

## RequestParams

传递一个对象至 requestParams 定义单个页面的属性

```

// 用于匹配指定的路径，支持使用正则表达式。
String urlPattern;                      

// 可选，的标题
String title;

// 可选，的背景色，页面回调时，可以看到，使用 hex 方式传入，如 "#000000"(RGB)，或 "#00000000"(ARGB)
String backgroundColor;

// 可选，状态栏是否隐藏
BOOL statusBarHidden;

// 可选，状态栏的样式，"light" 代表白色, "default" 代表黑色 (iOS only)
String statusBarStyle;

// 可选，导航栏是否隐藏
BOOL navigationBarHidden;

// 可选，导航栏分隔线是否隐藏
BOOL navigationBarSeparatorHidden;

// 可选，导航栏背景色，使用 hex 方式传入，如 "#000000"(RGB)，或 "#00000000"(ARGB)
String navigationBarBackgroundColor;

// 可选，导航栏文字、图标渲染色，使用 hex 方式传入，如 "#000000"(RGB)，或 "#00000000"(ARGB)
String navigationBarTintColor;

// 可选，是否布局至最顶端
BOOL fullScreenContent;

// 可选，是否允许使用回弹效果 (iOS only)
BOOL allowBounce;

// 可选，是否显示滚动条
BOOL showsIndicator;


```

* 将对象置于 Array 并放置到 requestParams.items 字段中，可以批量配置。
* urlPattern 为空，则表示，设置当前页面。

## Sample

```
var setting = JSMessage.newMessage();
setting.moduleName = "UI.Page";
setting.requestParams = {
    urlPattern: "http://duowan.cn/*",
    title: "多玩游戏",
    navigationBarHidden: false,
    statusBarStyle: "default",
    statusBarHidden: false,
    navigationBarBackgroundColor: "#000000",
    navigationBarTintColor: "#ffffff",
    navigationBarHidden: true,
    backgroundColor: "#f2f2f2",
};
setting.call();
```