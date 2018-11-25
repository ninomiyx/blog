# Vue.js Hello World

Vue 是一个框架，可以帮助开发者很简单的通过模版语言将数据渲染到 DOM 上面。[这里](https://scrimba.com/p/pXKqta/cQ3QVcr)是 Vue.js 到一个 Hello World 教程。

第一步，在网页前面到 `head` 标签插入 `<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>`，这样就可以在网页加载的时候，加载 Vue.js 框架。

第二部，在 `body` 标签内，插入模版：

```html
<div id = "app">
    {{message}}
</div>
```

其中，`{{变量}}` 调用 `vue`, `变量` 可在 `js` 中更改。

最后，在我们自己的 JavaScript 写以下代码：

```js
var app = new Vue({
    el: `#app`,
    data: {
        message: `Hello World`
    },
});
```

稍微解释一下 Vue.js 的 option 基本参数：

- `el`： 标签的选择器，这里 `#app` 意思是，选择 `id` 为 `app` 的标签，也就是上面的 `<div id="app" />`
- `data`： 数据对象 `{}`，要渲染的数据。
- 最后，新建一个 `Vue` 对象 `new Vue({});`，页面就可以渲染了。



## Countdown

扩展一下，写一个倒计时，JavaScript 的代码可以写成这样：

```js
var time = 10;
var countDown = function () {
    time = time - 1;
    if (time >= 0) {
        app.message = "remains: " + time;
    } else {
        app.message = "time out";
    }
};

setInterval(countDown, 1000);
```

这里使用到了 `setInterval` 函数， 它的使用方式是这样的： `setInterval(函数, 毫秒)`。

## Show time

类似的，写一个显示当前时间的功能：

```js
setInterval(time,1000);
function time() {
    var now = new Date(); // 创建一个时间日期对象，默认值是当前时间
    app.message = now.toLocaleTimeString();
}
```
