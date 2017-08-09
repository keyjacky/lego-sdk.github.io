# Skeleton

使用 WebView.Skeleton 可以在避免 WebView 加载过程中出现白屏的尴尬情况。

## 主动 Skeleton

原理：提前将 targetURL 中的内容，使用 snapshotURL 加载并截屏，当 targetURL 要显示时，则先将截图置于白屏 WebView 上作为 Skeleton。

在任何页面，使用以下方式，保存截屏。

```js
JSMessage.newMessage("WebView.Skeleton", {opt: "snapshot", targetURL: "http://xxx.com/target.html", snapshotURL: "http://xxx.com/snapshot.html"}).call(null);
```

* targetURL 和 snapshotURL 只支持以 ```http://``` ```https://``` ```file://``` 开头的完整路径。

## 被动 Skeleton

原理：WebView 加载成功前，一个 skeleton.html 的页面会被优先加载，并显示在屏幕上。

在页面加载完成时，skeleton.html 会被隐藏，你也可以手动控制 skeleton.html 隐藏的时机。

### skeleton.html

skeleton.html 应该被放置在 iOS 的应用包中，Android 的 assets 目录下。

skeleton.html 没有任何 LEGO-SDK 的执行权限。

skeleton.html 模板如下

```html
<!DOCTYPE html>
<html lang="en">
<body>
    ...
</body>

<script>
    
    function canHandleRequest(url) {
        // 通过 url 来判断，返回 true 代表，skeleton.html 应该出现在白屏阶段。
        if (url.startsWith('http://duowan.cn/')) {
            return true;
        }
        return false;
    }

    function handleRequest(url) {
        // 响应 url 的请求，并更改 skeleton.html 内容。
        // 返回 true 代表，你需要自行控制 skeleton.html 消失的时机。
        // 默认应该返回 false，代表 WebView 加载完成后，skeleton.html 自动消失。
        return false;
    }
    
</script>

</html>
```

## 隐藏 Skeleton

正常情况下，Skeleton 会在 WebView 加载完成后消失。

### 主动 Skeleton

可以使用以下方法，提前隐藏 Skeleton，否则 Skeleton 会在 WebView 加载完成后消失。

```js
JSMessage.newMessage("WebView.Skeleton", {opt: "dismiss"}).call(null);
```

### 被动 Skeleton

但是，当 ```skeleton.html``` 中的 ```handleRequest``` 方法返回 ```true``` 时，需要使用以下方法，手动隐藏 Skeleton。

```js
JSMessage.newMessage("WebView.Skeleton", {opt: "dismiss"}).call(null);
```