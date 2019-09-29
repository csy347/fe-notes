# HTML移动端及PC端页面适配跳转

    网页通常需要适配PC端和移动端，适配可以通过响应式布局判断屏幕尺寸来展示不同的效果，还可以通过编写两个页面，也就是PC端和移动端分别写一个页面，这种方式更方便功能模块的编写。

　　通常情况下，PC端域名使用www，而移动端域名使用m，在编写PC和移动两个页面时，在实际页面加载时要加载到对应的页面，所以需要判断设备的类型，让搜索引擎和浏览器知道，PC端用户应该访问哪个页面，移动端用户应该访问哪个页面。

　　自适应页面，在页面头部添加一行：`<meta name="applicable-device" content="pc,mobile">`

　　PC页面，在页面头部添加一行：`<meta http-equiv="mobile-agent" content="format=xhtml; url=https://m.williamlong.info/">

　　PC页面，在页面底部增加Javascript代码，将移动设备访问流量跳转到移动网站，例如：

``` javascript
!function () {
var devices = ["iPhone","Android","Windows Phone"]
var ua = window.navigator.userAgent
for (var i = 0; i < devices.length; i++) {
if (ua.indexOf(devices[i]) != -1) {
    window.location.href = 'https://www.williamlong.info'
}
}
}()
```

## 参考

- https://www.williamlong.info/archives/5787.html
