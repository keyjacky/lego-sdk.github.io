# ImagePreviewer

使用 ImagePreviewer 可以调起原生的图片浏览器，以提供更流畅的大图预览体验。
同时，使用该浏览器，可以保存、复制大图。

## RequestParams
```
String[] URLs;
String   currentURL;
```
## ResponseParams

## Example

```javascript
var URLs = [
    "http://s1.dwstatic.com/group1/M00/5D/7B/6efd4050b5dc9269f6576e2c67e1abdd.jpg",
    "http://s1.dwstatic.com/group1/M00/48/0A/84fd8208a2e519d9678d58f55cf15d02.jpg",
    "http://s1.dwstatic.com/group1/M00/99/7C/b588c7bb9978650f195d77102e3c8b99.jpg",
    "http://s1.dwstatic.com/group1/M00/0C/B9/75fac5cd0a03ad69be4e5c0e67248b87.jpg"
]
var currentURL = "http://s1.dwstatic.com/group1/M00/5D/7B/6efd4050b5dc9269f6576e2c67e1abdd.jpg"
JSMessage.newMessage("UI.ImagePreviewer", {
    URLs: URLs,
    currentURL: currentURL
}).call(null)
```
