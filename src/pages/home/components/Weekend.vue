<template>
  <div>
    <div class="weekend-title">周末推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item in recommendList"
                :key="item.id"
      >
      <div class="item-img-wrapper">
        <img :src="item.imgUrl"  class="item-img">
      </div>
      <p class="item-title">{{item.title}}</p>
      <p class="item-desc">{{item.desc}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "HomeWeekend",
    data(){
      return {
        recommendList: [{
        id: '001',
        imgUrl: 'http://img1.qunarzz.com/sight/source/1505/7d/df6ff468331c43.jpg_r_640x214_1f3783d0.jpg',
        title: "宋豇豆角",
        desc: "登录客户端客服"
      },{
        id: '002',
        imgUrl: 'http://img1.qunarzz.com/sight/source/1603/ad/69b0fc5f48ad5f.jpg_r_640x214_b0fd5c7b.jpg',
        title: "宋豇豆角",
        desc: "登录客户端客服"
      },{
        id: '003',
        imgUrl: 'http://img1.qunarzz.com/sight/source/1511/1d/fe098e8cfec117.jpg_r_640x214_a9be292a.jpg',
        title: "宋豇豆角",
        desc: "登录客户端客服"
      }]
      }
    }
  }
  
</script>

<style scoped lang="stylus">
  .weekend-title
    margin-top: .2rem
    background: #ccc
    line-height: .6rem
    text-indent: .3rem
    border-radius: .02rem
  .item-img-wrapper
    overflow: hidden
    height: 0
    padding-bottom: 33.9% 
    .item-img
      width: 100%  
  .item-title
    line-height: .54rem
    font-size: .32rem
    padding-left: .3rem
  .item-desc
    line-height: .4rem
    color: #ccc
    padding-left: .3rem
    padding-bottom: .1rem
</style>