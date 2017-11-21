# iOS

集成 LEGO-SDK 最简单的方式是使用 CocoaPods

## 全部集成

你可以一次集成所有模块，只需要将以下依赖添加至 Podfile 即可。

```
pod "LEGO-SDK"
```

## 部分集成

你也可以根据需要集成相应模块，将以下依赖按需添加至 Podfile。

```
pod 'LEGO-SDK/Core'
pod 'LEGO-SDK/API/Native/Check'
pod 'LEGO-SDK/API/Native/Device'
pod 'LEGO-SDK/API/Native/FileManager'
pod 'LEGO-SDK/API/Native/HTTPRequest'
pod 'LEGO-SDK/API/Native/Notification'
pod 'LEGO-SDK/API/Native/OpenURL'
pod 'LEGO-SDK/API/Native/Pasteboard'
pod 'LEGO-SDK/API/Native/UserDefaults'
pod 'LEGO-SDK/API/UI/ActionSheet'
pod 'LEGO-SDK/API/UI/AlertView'
pod 'LEGO-SDK/API/UI/ImagePreviewer'
pod 'LEGO-SDK/API/UI/Refresh'
pod 'LEGO-SDK/API/UI/NavigationController'
pod 'LEGO-SDK/API/UI/NavigationItem'
pod 'LEGO-SDK/API/UI/ModalController'
pod 'LEGO-SDK/API/UI/PageState'
pod 'LEGO-SDK/API/UI/Picker'
pod 'LEGO-SDK/API/UI/Toast'
pod 'LEGO-SDK/API/WebView/Pack'
```

## 启动 WebView

创建一个 LGOBaseViewController 的实例，并将目标 url 赋值到对应属性，然后 Push 或者 Present 出来即可。

```objectivec
LGOBaseViewController *viewController = [LGOBaseViewController new];
viewController.url = @"http://webpage.yy.com/s/lego-sdk/orz.html";
[self.navigationController pushViewController:viewController animated:YES];
```

* ```http://webpage.yy.com/s/lego-sdk/index.html``` 是一个调试页面，可供测试使用。

## 白名单

我们使用白名单的机制，确保只有受信的网站才能发起 SDK 请求，如未设置任何白名单，则任何网站都可以发起请求。

要为 SDK 设置网站白名单，使用以下方法（一般在 AppDelegate 中执行）。

```
[[LGOCore whiteList] addObject:@"webpage.yy.com"];
```

* 注意，子域名亦在白名单内，即添加 webpage.yy.com，那么 map.webpage.yy.com 也会同样生效。
* 注意，只需要添加域名或 IP 即可，不需要添加协议头（如 ```http://```），也不需要添加端口号（如 ```:8080```）
