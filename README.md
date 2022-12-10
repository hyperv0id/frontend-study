# frontend-study
学前端，认识前端

## 1-vue 引言

> **渐进式** JavaScript 框架

1. 渐进式
    1. 易用 会html+js+css就会vue
    2. 高效 效率高
    3. 灵活

### 后端视角

vue 能让我们操作很少的 dom 就很容易实现数据试图绑定

PS: vue 不希望引入 jQuery 框架

## 2-vue入门

### 2.1-下载

#### npm

```bash
$ npm install vue
```

#### html引入

```html
<script src="https://cdn.jsdelivr.net/npm/vue@2.6.14"></script>
```

### 2.2-get started

一个简单 vue 案例：

- el: 指定 vue 实例的作用域
- data: 指定 vue 实例的数据
- `{{变量名}}`: 替换，vue 会自动替换里面的内容，动态渲染
    - 注意作用域外的不会被渲染
    - 不仅同名的内容可以渲染，表达式也可以渲染，eg: `{{ 1+1 }}` 输出 `2`

```html
<div id="app">
    <p>你好 cjj</p>
    <p>{{msg}} cjj</p>
</div>

<!-- 引入 vue.js 脚本 -->
<script src="https://cdn.jsdelivr.net/npm/vue@2.6.14"></script>
<script>
    const app = new Vue({
        // el属性，用于给 vue 实例定义作用域
        el : "#app",
        // data 属性，给vue实例定义相关数据
        data: {
            msg: "hello"
        }
    });
</script>
```

## 3- `v-text` 和 `v-html`

- 两者都会替换（抹除）标签内部信息，而 `{{}}` 不会
- `v-text`: 只会替换文字，类似 js 中的 `innerText`
- `v-html`: 不仅会替换文字，还会以 html 格式被渲染，类似 js 中的 `innerHTML`

```html
<div id="app">
    <p>你好 cjj</p>
    <p>{{msg}} cjj</p>
    <p v-text="msg"> cjj</p>
    <p v-html="html_msg"> cjj</p>
</div>

<!-- 引入 vue.js 脚本 -->
<script src="https://cdn.jsdelivr.net/npm/vue@2.6.14"></script>
<script>
    const app = new Vue({
        // el属性，用于给 vue 实例定义作用域
        el : "#app",
        // data 属性，给vue实例定义相关数据
        data: {
            msg: "hello",
            html_msg: "<div style='color: red'>hello</div>"
        }
    });
</script>
```

**输出**：
![](https://pic-1257412153.cos.ap-nanjing.myqcloud.com/images/images/2022/12/10/20221210213142-79700f.png)


## 4-vue中事件的定义和使用

### 4.1-绑定事件语法

**语法**：`v-on:[事件名]="函数"`。

事件名有 `click`、`keydown`、`keypress` 等

**注意**：函数/函数的参数需要在vue中或者为全局

```html
<div id="app">
    <input type="button" value="clickme!!!" v-on:click="alert(msg);">
    <input type="button" value="some_function" v-on:click="some_function();">
</div>

<!-- 引入 vue.js 脚本 -->
<script src="https://cdn.jsdelivr.net/npm/vue@2.6.14"></script>
<script>
    const app = new Vue({
        // el属性，用于给 vue 实例定义作用域
        el : "#app",
        // data 属性，给vue实例定义相关数据
        data: {
            msg: "hello"
        },
        methods:{
            some_function(){
                alert("egg #UNKNOW");
            }
        }
    });
</script>
```


