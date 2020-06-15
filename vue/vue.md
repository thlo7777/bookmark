## VUE  资料

#### [看完这篇，我奶奶都会设计组件了](http://maying.ink/2019/07/29/part/)

## v-html
---
在 html 中输出 data 中的值了，我们已经用的是{{xxx}},这种情况是有弊端的，就是当我们网速很慢或者 javascript 出错时，会暴露我们的{{xxx}}。 Vue 给我们提供的 v-text 和 v-html,就是解决这个问题的。我们来看代码：
```
vuejs {{}}，v-text 和 v-html的区别
<div id="app">
　　<p>{{message}}</p> <!-- 输出：<span>通过双括号绑定</span> -->
　　<p v-html="html"></p> <!-- 输出：html标签在渲染的时候被解析 -->
　　<p v-text="text"></p> <!-- 输出：<span>html标签在渲染的时候被源码输出</span> -->
</div>


<script>
　　let app = new Vue({
　　el: "#app",
　　data: {
　　　　message: "<span>通过双括号绑定</span>",
　　　　html: "<span>html标签在渲染的时候被解析</span>",
　　　　text: "<span>html标签在渲染的时候被源码输出</span>",
　　}
});
</script>


区别：
{{message}}：将数据解析为纯文本，不能输出真正的html，在页面加载时显示{{}}，所以通常使用v-html和v-text代替，且花括号方式在以后可能被取消

v-html="html"：输出真正的html

v-text="text"：将数据解析为纯文本，不能输出真正的html，与花括号的区别是在页面加载时不显示{{}}
 
```
#### [解决v-html指令潜在的xss攻击](https://juejin.im/post/5d5924a0e51d4561fc620a46)

#### [vscode 新建vue模板步骤](https://juejin.im/post/5d3137e26fb9a07eca69b4a7)
> ``` data是每个组件的私有内存，可以在其中存储需要的任何变量。props是将数据从父组件传递到子组件的方式。 props 单向流动，父组件到子组件。 data是每个组件的内存,这是存储数据和希望跟踪的任何其他变量的地方。 ```
 一般情况下  此处的data是私有的，仅供组件本身使用，其他组件不能访问它。 注意:理论上是其它组件是不能访问这些数据，但实际是可以的。但是出于同样的原因，这样做是非常糟糕的 


#### [vue---获取元素额外生成的data-v-xxx](https://blog.csdn.net/maidu_xbd/article/details/89315210)
> ``` 当 <style> 标签有 scoped 属性时，它的 CSS 只作用于当前组件中的元素。编译时将生成data-v-xxx属性，如下的“data-v-2bc3d899”就是因为加了scoped. ```
> ``` 
> <style scoped>
> .title {
>  color:blue;
> }
> </style>
> <template>
>  <div class="title">hello</div>
> </template>
> ```

>上述代码被编译为：
> ``` 
> <style>
> .title[data-v-f3f3eg9] {
>  color: blue;
> }
> </style>
> <template>
>  <div class="title" data-v-f3f3eg9>hello</div>
> </template>
> ```

### npm install packages path 
> ```
> npm root -g
> C:\Users\lxw77\AppData\Roaming\npm\node_modules
> npm install grunt # 本地安装
> npm install -g grunt-cli # 全局安装
> ```

> 本地安装: 
> ```
> 1、将安装包放在 ./node_modules 下（运行npm时所在的目录）
> 比如运行下面命令
> npm install grunt --save-dev
> 那么，就会在当前目录下发现一个node_modules目录，进去后能够看到grunt这个包
> ```


### Vue cli4  按需加载 ant design 组件
> ```
> 1.安装 Vue cli4
>   $ npm install -g @vue/cli
> 2. 创建新项目
>   $ vue create antd-demo
> 3. 进入项目并启动
>   $ cd antd-demo
>   $ npm run serve
> 4. 安装ant design
>   $ npm install ant-design-vue --save
> 
> 5. 使用 babel-plugin-import（推荐）
> 5.1  安装 
>   $ npm install babel-plugin-import --save-dev
> 5.2 使用 vue-cli 3 的小伙伴 #
>     修改babel.config.js文件，配置 babel-plugin-import
>   module.exports = {
>       presets: ["@vue/app"],
>       plugins: [
>           [
>               "import",
>               { libraryName: "ant-design-vue", libraryDirectory: "es", style: true }
>           ]
>       ]
>   };
> 6. 引入局部组件 main.js
> import Vue from 'vue'
> import App from './App.vue'
> import router from './router'
> import store from './store'
> import {
>     Menu,
>     Button,
>     Icon,
>     Layout
> } from 'ant-design-vue'

> Vue.use(Menu)
> Vue.use(Button)
> Vue.use(Icon)
> Vue.use(Layout)

> Vue.config.productionTip = false

> new Vue({
>    router,
>    store,
>    render: h => h(App)
> }).$mount('#app')
> ```