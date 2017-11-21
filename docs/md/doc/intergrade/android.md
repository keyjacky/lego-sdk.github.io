# Android

集成 LEGO-SDK 最简单的方式是使用 Gradle

## 添加依赖

添加 Jitpack 仓库至 build.gradle

```
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```

请根据需要，将对应依赖添加至 Gradle 文件。

```
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:core:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:native.check:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:native.device:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:native.filemanager:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:native.httprequest:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:native.notification:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:native.openintent:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:native.pasteboard:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:native.userdefaults:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.actionsheet:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.alertview:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.imagepreviewer:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.modalcontroller:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.navigationcontroller:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.navigationitem:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.page:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.pagestate:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.picker:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.refresh:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:ui.toast:1.0.8'
compile 'com.github.LEGO-SDK.LEGO-SDK-Kotlin:webview.pack:1.0.8'
```

## ProGuard 规则

如需代码混淆，请添加以下规则至 proguard-rule.pro

```
-keep public class * extends com.opensource.legosdk.core.LGOModule
-keepclassmembers public class * extends com.opensource.legosdk.core.LGOModule {
    public *;
}
```

## 启动 WebView

使用以下方法，可在任意 Activity 启动一个 WebViewActivity。

```java
LGOWebViewActivity.Companion.openURL(MainActivity.this, "http://webpage.yy.com/s/lego-sdk/orz.html");
```

* ```http://webpage.yy.com/s/lego-sdk/index.html``` 是一个调试页面，可供测试使用。

## 白名单

我们使用白名单的机制，确保只有受信的网站才能发起 SDK 请求，如未设置任何白名单，则任何网站都可以发起请求。

要为 SDK 设置网站白名单，使用以下方法（一般在 Applcation:onCreate 中执行）。

```
LGOCore.Companion.getWhiteList().add("webpage.yy.com");
```

* 注意，子域名亦在白名单内，即添加 webpage.yy.com，那么 map.webpage.yy.com 也会同样生效。
* 注意，只需要添加域名或 IP 即可，不需要添加协议头（如 ```http://```），也不需要添加端口号（如 ```:8080```）
