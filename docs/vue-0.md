# Vue.js Hello World

Vue 是一个框架，可以帮助开发者很简单的通过模版语言将数据渲染到 DOM 上面。[这里](https://scrimba.com/p/pXKqta/cQ3QVcr)是 Vue.js 到一个 Hello World 教程。

第一步，在网页前面到 `head` 标签插入 `<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>`，这样就可以在网页加载的时候，加载 Vue.js 框架。

第二步，在 `body` 标签内，插入模版：

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

## Condition
接下来，[这里](https://scrimba.com/p/pXKqta/cEQe4SJ)是Vue.js的一个condition教程。

在 `body` 中添加模板：

```html
 <div id="app">
    <span v-if="seen">Now you see me</span>
</div>
```

其中，`v-` 指的是在 `Vue` 中特定的条件语句。

接着，在我们自己的 JavaScript 写以下代码：
```js
var app = new Vue({
  el: '#app',
  data: {
    seen: true
  }
})
```

当且仅当 `seen` 的指为 `true` 时，对应的 `span` 标签才会显示。

## Countdowm

扩展一下，如果刚才的例子用上述的条件模板，代码则可以改为：

```html
<div id="app">
    <span v-if="progressing">Remians: {{timeLeft}}s.</span>
    <span v-if="ended">Timeout.</span>
</div>
```

JavaScript中可改为：

```js
var app = new Vue({
  el: '#app',
  data: {
    timeLeft : 10,
    progressing: true,
    ended : false,
  }
});

function countDown() {
  app.timeLeft = app.timeLeft - 1;
  app.progressing = app.timeLeft >= 0;
  app.ended = app.timeLeft < 0;
}

setInterval(countDown, 1000);
```


## For loops

[这里](https://scrimba.com/p/pXKqta/cB4gESW) 是`Vue.js`的一个`for`循环教程。

在`body`中添加模板：
```html
<div id="app">
    <ol>
        <li v-for="todo in todos">
        {{ todo.text }}
        </li>
    </ol>
</div>
```
- `<ol>`：有序排列标签，`1,2,3……`<br>
  `<ul>`：无序排列标签，`·`
- `<li>`：列表项，list items
- `v-for="a in b"`：`b`为赋值范围。

接着，在`JavaScript`中写下以下代码：
```js
var app = new Vue({
  el: '#app',
  data: {
    todos: [
      { text: 'Learn JavaScript' },
      { text: 'Learn Vue' },
      { text: 'Build something awesome' }
    ]
  }
});
```
其中，若想添加`todos`的幅值范围，除了直接在上面`data`中加，还可以以以下方式：
```js
app.todos.push({ text: 'New item' })
```

## 用户输入
### on-click

[这里](https://scrimba.com/p/pXKqta/czPNaUr)是用户点击button，并回馈交互的教程。

在`body`中添加模板：
```html
<div id="app">
    <p>{{ message }}</p>
    <button v-on:click="reverseMessage">Reverse Message</button>
</div>
```
接着，在`JavaScript`中写下以下代码：
```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
```
- `methods`：这个参数是用来放函数的，`function`
- `this`：当前的上下文
- `split('')`：拆开分解，eg，`abc` --- `"a""b""c"`，`split(`-`)`，拆解后则为`a-b-c`
- `reverse()`：反转，abc ---- cba
- `join('')`：和在一起，与`split`类似

### V-model

实现表单输入和应用状态之间的双向绑定，即改变`v-model`中`message`的内容，其他位置的`message`会跟着改变。点击[这里](https://scrimba.com/p/pXKqta/c9ePQT3)查看视频教程。

在`body`中添加模板：
```html
<div id="app">
    <p>{{ message }}</p>
    <input v-model="message">
</div>
```

接着，在`JavaScript`中写下以下代码：
```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

