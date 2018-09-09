# vue-travel

## 项目前置
开发环境:
```
  npm
  node
  vscode
  vue-cli
  axios
```
项目文件目录：
> README.md 说明文档 <br>
  package.json 项目依赖包<br>
  LICENSE 开源协议声明<br>
  src 源文件<br>
  .babelrc 代码转义<br>
  static 静态资源<br>
  config 项目配置文件<br>
  build 项目打包配置文件<br>
  ....<br>
  相关模板文件

## 单文件组件与路由
router
```
  new Vue({
    el: '#app',
    router,
    components: {App},
    template: '<App/>'
  })
```
路由：根据网址的不同返回不同的内容返回给用户<br>
在`main.js`发现找到了一个App组件，就会渲染`App.vue`中的内容，`App.vue`内有一个跳转，`<router-view>`实现跳转相对应的组件。<br>
`<router-view>`当前路由地址所对应的那个组件(到index.js里面去找相关的组件).
* 多页面
  *  首屏时间快，SEO效果好
  *  页面之间的切换比较慢
* 单页面
  * 首屏时间较慢，SEO效果不好
  * 减少DOM的加载,页面切换比较快
```javascript
  <div>
    <div class="home">home</div>
    <router-link to="/list">点击跳转</router-link>
  </div>
//单页面应用的跳转
```  
## 项目初始化
1. 引入reset.css
```
  (main.js入口文件) import "./assets/styles/reset.css"
```
2. 解决1px边框问题，引入border.css
```
  import "./assets/styles/border.css"
```
3. 引入fastClick 解决移动端300ms延迟问题
```javascript
  npm i fastclick --save-dev

  import fastClick from 'fastclick'
  fastClick.attach(document.body)
```
4. 引入图标文件iconfont
保留：eot,svg,ttf,woff文件
```
  import "@/assets/styles/iconfont/icontfont.css"
```
修改相对应的路径，引入成功。<br>
在styles目录下创建：`varibles.styl`全局变量,在某一个文件中单独引入：
```
  import "~@/assets/styles/iconfont/varibles.styl"
```
在单独的css文件中，引入全局变量`($bgColor)`就可以使用了。
5. 引入stylus,方便书写css文件
```
  npm i stylus --save
  npm i stylus-loader --save
```
### 组件目录
1. Home
   * componente/Header.vue
   * componente/Swiper.vue
   * componente/Icon.vue  
   * componente/Recommend.vue  
   * components/Weekend.vue
2. City
   * components/header.vue
   * components/search.vue 
3. axios发送数据请求
4. Detail
   * component/Banner.vue
### 组件介绍
1. HomeSwiper
```
安装： npm i vue-awesome-swiper@2.6.7 --save
引入VueAwesomeSwiper:
 import "xxx"
 import 'swiper/dist/css/swiper.css'
 Vue.use(VueAwesomeSwiper)
```
实现宽高比自适应（解决低速网络下的图片刷新bug）
```
  <div class="wrapper"></div>
  .wrapper
    overflow: hidden
    width: 100%
    height: 0
    padding-bottom: 实际宽度/实际高度
```
设置swiper-pagination的颜色
```
  .wrapper>>>.swiper-pagination-bullet
    background: #fff!important
```
2. HomeIcon
Icon页面切换逻辑实现
```javascript
  computed:{
    pages(){
      const pages = []
      this.iconList.forEach( (item,index)=>{
        const page = Math.floor(index/8) //数据的下标大于7的时候page=1
        if( !pages[page] ){
          pages[page]=[]
        }
        pages[page].push( item )
      })
      return pages
    }
  }

  <swiper-slide v-for="(page, index) in pages" :key="index">
//当页面的数据超过8个icon的时候就会切换到下一页面。
```
3. axios发送数据请求
```javascript
   methods: {
    getHomeInfo(){
      axios.get('/api/index.json')
       .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc(res){
      const data = res.data
      this.city = data.city
      this.swiperList = data.swiperList
    }
  },
  mounted(){
    this.getHomeInfo()
  }
//发送数据请求
```
把`/static/mock/index.json`替换成`/api/index.json`<br>
使用proxy配置项✅：
```
config>index.js

proxyTable: {
  '/api': {
    target: "http://localhost:8080",
    pathRewrite: {
      '^api':'/static/mock'
    }
  }
}
```
主要是用户访问的过程中，Vue自动帮我们做一个开发环境的转发.<br>
使用ajax获取到的数据传递从父组件传递给子组件:
```
父组件传递：
  <home-header :city="city" ></home-header>
  
  data(){
    return{
      city: ''
    },
  }
子组件接收:
  props:{
    city: Array
  }
```
4. CitySearch
```
  <div class="search">
    <input type="text" class="search-input"
    placeholder="输入城市名或者拼音">
  </div>
```
5. CityList
使用better-scroll进行滚动
```
  npm i better-scroll --save
```
```javascript
使用：
  最外层要有<div>
  <div class="list" ref="wrapper">
引入：
  import BScroll from 'better-scroll'
定义：
mounted(){
      this.scroll = new BScroll(this.$refs.wrapper)
    }
```
## 兄弟组件联动
1. 子(弟弟)组件先把数据传递给父组件
2. 父组件再将数据传递给需要的(兄弟)兄弟组件
```
子组件传递给父组件：(向外触发$emit事件)
  @click="handleLetterClick"
  handleLetterClick(e){
    this.$emit("change" , e.target.innerHTML )
  }
//子组件向外触犯一个change事件

父组件接收：
  @change=" handleLetterChange"

methods: {
  handleLetterChange(letter){
    console.log(letter)  //打印：a b c d
  }
}

父组件再向子(哥哥)组件传递输出
<city :letter="letter">

哥哥组件接收：
props: {
  letter: String
}
```
解决多页面进入刷新跳转问题：
```javascript
router->index.js路由最后加
  scrollBehavior (to, from , savedPosition){
    return { x:0 , y: 0 }
  }
```