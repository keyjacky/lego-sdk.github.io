# Pack

Pack 模块为 WebView 提供打开一个 ZIP 包的能力。

当这个 ZIP 压缩包包含一个网站时，WebView 会打开该网站。

## 使用方法

1. 使用 https://github.com/LEGO-SDK/LEGO-Pack 工具打包网站，然后将 xxx.zip 和 xxx.zip.hash 上传到服务器。
2. 按照正常的方法，使用 WebView 打开这个 zip 包。

```
// iOS
[webView loadRequest:[NSURLRequest requestWithURL:[NSURL URLWithString:@"http://domain.com/xxx.zip"]]];
```

```
// Android
webView.loadUrl("http://domain.com/xxx.zip");
```

## 本地缓存

* 你可以将 ZIP 放置到 iOS 工程目录下；
* 你可以将 ZIP 放置到 Android 工程 Assets 目录下；
* 在离线、缓存失效、首次加载的情况下，应用内的 ZIP 文件将会被使用。

## 远程更新

* 在远程 ZIP 包与本地 ZIP 包存在差异时（这个差异是通过 md5 对比实现的），本地缓存会被更新。

## 注意事项

* ZIP 包中根目录必须包含 index.html 文件；
* hash 文件必须上传一同上传。