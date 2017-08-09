# Preload

使用 Preload 可以加速 WebView 加载

## 原理

Preload 会在后台创建一个 Ready 好的 WebView，当符合条件时，会优先使用该 WebView 加载新的网页。

## 参数 

url: String    // 预加载的网页
token: String  // 标识符，将这个标识符传递至 UI.NavigationController 或 UI.ModalController 中，即可达到 Preload 的效果。

## Usage

```js
JSMessage.newMessage("WebView.Preload", {url: "http://yourserver/xxx.html", token: "testToken"}).call()
```