## VUE  资料

### Axure RP9 license 
> ```
> Axure RP 9.0.0.3693，3695，3696，3699版本使用—-亲测可用
> Licensee : sunny_pm 【推荐，我一直在用的这个 好多版本都可以用】
> KEY: P0qe+ILVbfoor6qQXv32NDzicDpygaWWrBt+FW4lWnU=
> ```

#### [看完这篇，我奶奶都会设计组件了](http://maying.ink/2019/07/29/part/)

### v-html
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

### ant-design-vue组件的三种加载方式
>```
>1. 完整引入, main.js中全局引入并注册, 在页面中不再需要引入注册组件，可以直接使用所有的组件
> import Antd from 'ant-design-vue'
> import 'ant-design-vue/dist/antd.css'
> Vue.use(Antd)
> -----------
>2. 导入部分组件,  在main.js中导入并注册需要在项目中使用的组件
>  import { Button } from "ant-design-vue";
>  import 'ant-design-vue/lib/button/style/css'
>  Vue.component(Button.name, Button) 
>  在项目中可以直接使用这个已经注册的组件
>  <template>
>    <div>
>        <a-button type="primary">hello world</a-button>
>    </div>
>  </template>
>
>  <script>
>   export default {}
>  </script>
> -----------
>3. 按需加载  在需要使用相关组件的页面引入并注册即可按需加载.  或者在main.js中全局引入
>  <script>
>  // @ is an alias to /src
>  import HelloWorld from '@/components/HelloWorld.vue'
>  import { Row, Col } from 'ant-design-vue' //import Grid
>  export default {
>    name: 'Home',
>    components: {
>      HelloWorld,
>      ARow:Row,
>      ACol:Col
>    }
>  }
>  </script>
>```

## less 和 Mixin介绍

> #### [Less介绍及其与Sass的差异](https://www.sass.hk/skill/sass5.html)
> #### [less-Mixin 之 @functions 趣谈](https://www.geek-share.com/detail/2791518135.html)
>> ```
>> .paletteMixin() {
>> @functions: ~`(function() {
>> this.palette = function(color) {
>> return color;
>> }
>> })()`;
>> }
>> ```

#### [vue-cli4 全面配置(持续更新)](https://github.com/staven630/vue-cli4-config)

#### VUE编程规范
>```
> 指令缩写 (用 : 表示 v-bind: 、用 @ 表示 v-on: 和用 # 表示 v-slot:) 应该要么都用要么都不用。
> script标签内部解构顺序
>> components --> props --> data --> computed --> watch --> filter --> 钩子函数 --> methods 
>```


#### [Grid Layout Editor for Vue.js — A research project for Pariksha.io](https://blog.prototypr.io/grid-layout-editor-for-vue-js-a-research-project-for-pariksha-io-e3445025d21e)
```
github link address 
```

#### vue中的.sync修饰符用法及原理详解
```
vue中我们经常会用v-bind(缩写为:)给子组件传入参数。
或者我们会给子组件传入一个函数，子组件通过调用传入的函数来改变父组件的状态。
例如：

//父组件给子组件传入一个函数
 <MyFooter :age="age" @setAge="(res)=> age = res">
 </MyFooter>
 //子组件通过调用这个函数来实现修改父组件的状态。
 mounted () {
      console.log(this.$emit('setAge',1234567));
 }

这时子组件触发了父组件的修改函数使父组件的age修改成了1234567

这种情况比较常见且写法比较复杂。于是我们引出今天的主角 .sync

这时我们可以直接这样写

//父组件将age传给子组件并使用.sync修饰符。
<MyFooter :age.sync="age">
</MyFooter>
//子组件触发事件
 mounted () {
    console.log(this.$emit('update:age',1234567));
 }
这里注意我们的事件名称被换成了update:age
update：是被固定的也就是vue为我们约定好的名称部分
age是我们要修改的状态的名称，是我们手动配置的，与传入的状态名字对应起来
```

#### vue vue.config.js 需要手动添加文件并配置

#### [複用元件的好幫手：Vue Slots(v-slot、Scoped Slots)](https://medium.com/unalai/%E8%A4%87%E7%94%A8%E5%85%83%E4%BB%B6%E7%9A%84%E5%A5%BD%E5%B9%AB%E6%89%8B-vue-slot-v-slot-scoped-slots-5364a0048ab7)

#### Vue el与$mount的区别
```
/* 此时是未挂载状态，页面是不显示的 */
//此时可以使用下面A或B来挂载，都可以
new Vue({
  router,
  store,
  render: h => h(App)
})

//A指定el option
new Vue({
  el: '#app',
  router,
  store,
  render: h => h(App)
})
//B使用$mount实例方法
new Vue({
  router,
  store,
  render: h => h(App)
}).$mount('#app')

/* 但是下面这种情况只能使用$mount挂载 */
//在vue实例化之后，再进行挂载

//这种方式是错误的，查看el限制（上面picture-el）
const vm = new Vue({
  router,
  store,
  render: h => h(App)
})

vm.$el = '#app';

//可以使用$mount来挂载
const vm = new Vue({
  router,
  store,
  render: h => h(App)
})

vm.$mount('#app')

```
#### VUE项目的目录的结构
```
### 目录结构如下：
demo1                                       # 工程名
|   |--- dist                               # 打包后生成的目录文件             
|   |--- node_modules                       # 所有的依赖包
|   |--- app
|   | |---index
|   | | |-- views                           # 存放所有vue页面文件
|   | | | |-- parent.vue                    # 父组件
|   | | | |-- child.vue                     # 子组件
|   | | | |-- index.vue
|   | | |-- components                      # 存放vue公用的组件
|   | | |-- js                              # 存放js文件的
|   | | |-- store                           # store仓库
|   | | | |--- actions.js
|   | | | |--- mutations.js
|   | | | |--- state.js
|   | | | |--- mutations-types.js
|   | | | |--- index.js
|   | | |-- app.js                          # vue入口配置文件
|   | | |-- router.js                       # 路由配置文件
|   |--- views
|   | |-- index.html                        # html文件
|   |--- webpack.config.js                  # webpack配置文件 
|   |--- .gitignore  
|   |--- README.md
|   |--- package.json
|   |--- .babelrc                           # babel转码文件
```

#### ...mapState一定也是写在computed里才有效大家千万要记住了
```
在组件调用vuex中的 值，我们一般会这样写：const value = this.$store.state.value

当我们在组件中调用几十个vuex中的值时，这样的写法显得有些重复繁琐。这时候mapstate就能发挥巨大作用了。

mapstate第一种用法：  第一种写法仅适用data无重名，无计算属性的组件
我们可以在组件内的计算属性中写成下面这个样子：
computed : mapState (["name", "value", "age"])

mapstate第二种用法： 第二种写法适合无计算属性的组件使用
第二种写法是第一种写法的升级版，这种写法解决的是data重名属性的问题，这里解决的方式是分别给每个state值重新起名。
computed : mapState ({
    storeName : state => state.name
    storeValue : state => state.value
    storeAge : state => state.age
})

mapstate第三种用法：
当我们既想使用mapState，又不想跟data重名，还想给别的计算属性挪地方的话，可以试试第三种写法。
这种写法是第二种写法的升级版，将mapState放到computed计算属性里面，用扩展运算符对mapState进行展开。
这种写法能完美解决上面两种方法带来的不便，data重名不怕、computed也留了空间。
computed : {
    ...mapState({
    storeName : state => state.name
    storeValue : state => state.value
    storeAge : state => state.age
    }),

    count(){
        ...
    },
}


两种对比
computed: {
  count () {
    return this.$store.state.count
  },
  name () {
    return this.$store.state.name
  }
},

使用...mapState
computed:{
  ...mapState(['count','name'])
},
```