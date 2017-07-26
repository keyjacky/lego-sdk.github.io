# Native

Native 提供的 API

* Call - 提供一条安全通道，使得 Javascript 可以直接调用原生代码。 (Universal)
* Check - 检查当前 SDK 允许 Javascript 调用的模块。 (Universal)
* DataModel - 在 WebView 中配置一个 Map 字典，Javascript / Native 可以更改这个 Map 中的数据，数据更改的同时，会触发事件回调。 (Universal)
* Device - 获取当前设备的信息。 (Universal)
* FileManager - 可以无限制地存取应用沙箱中的文件。 (Universal)
* HTTPRequest - 可以无限制地发起一个跨域请求。 (Universal)
* Notification - 可以在多个 WebView 之间进行通讯。 (Universal)
* OpenIntent - 可以调起一个 Intent，通过这种方式，可以打开一个应用。 (Android Only)
* OpenURL - 可以调起一个 URL，通过这种方式，可以打开一个应用。 (iOS Only) 
* Pasteboard - 可以将某段文本设置到系统剪贴板中，也可以从剪贴板中取出某段文本。 (Universal)
* UserDefaults - 可以存储用户配置信息，这些信息会在应用从手机中删除前，一直存在。 (Universal)