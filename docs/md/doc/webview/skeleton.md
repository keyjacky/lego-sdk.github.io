# Skeleton

使用 WebView.Skeleton 可以在避免 WebView 加载过程中出现白屏的尴尬情况。

WebView 加载成功前，一个 skeleton.html 的页面会被优先加载，并显示在屏幕上。

在页面加载完成时，skeleton.html 会被隐藏，你也可以手动控制 skeleton.html 隐藏的时机。

## skeleton.html

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

## Dismiss

当 ```handleRequest``` 返回 false 时，skeleton.html 会在 WebView 加载完成后消失。

否则，需要使用以下 API 控制 skeleton.html 的消失。

```
JSMessage.newMessage("WebView.Skeleton", {opt: "dismiss"}).call(null);
```