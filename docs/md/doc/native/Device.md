# Device

使用 Device 模块获取当前设备的信息

目前提供这些信息

* 设备名称
* 设备类型
* 设备标识
* 应用名称
* 应用标识
* 应用版本
* 应用构建号
* 是否正在使用WIFI
* 蜂窝数据类型（2G、3G、4G）

同时，原生应该还可以向 LGODevice.custom 存入 Key-Value，这些信息，会连同上面信息，一并返回给 WebView。

支持同步的方式获取返回结果，如果要获取最新的结果，仍然需要使用回调的方式。

## RequestParams

-

## ResponseParams

application:

* 类型 : JSON Object
* 描述 : 应用信息
* 内部字段 :

```
"application": {
    "name": appName, // 应用名称
    "bundleIdentifier": appBundleIdentifier, // 应用BundleId
    "shortVersion": appShortVersion, // 应用版本号
    "buildNumber": appBuildNumber, // 发布次数
}
```


device:

* 类型 : JSON Object
* 描述 : 设备信息
* 内部字段 :

```
"device": {
    "name": String, // 设备名称
    "model": String, // 设备型号
    "osName": String, // 操作系统
    "osVersion": String, // 操作系统版本号
    "IDFV": String, // 设备唯一ID, 类似UUID
    "screenWidth": Int, // 屏幕宽度
    "screenHeight": Int, // 屏幕高度
}
```

custom:

* 类型 : JSON Object
* 描述 : 应用自定义信息
* 内部字段 :

```
"custom": {
    "customKey": customValue,
}
```

network:

* 类型 : JSON Object
* 描述 : 网络状态
* 内部字段 :

```
"network": {
    "usingWIFI": Bool, // 是否使用wifi, 判断网络状态的时候需要先判断是否使用wifi
    "cellularType": Int, // 0 = 无网络, 2 = 2G, 3 = 3G, 4 = 4G
}
```

## Example

```javascript

// syncCall
var syncResult = JSMessage.newMessage("Native.Device").call()
console.log(syncResult)

// asyncCall
JSMessage.newMessage("Native.Device").call(function(meta, result) {
    if (meta.error){ return console.error(error); }
    console.log(result)
})

```