<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item in recommendList"
                :key="item.id"
      >
        <img :src="item.imgUrl"  class="item-img">
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "HomeRecommend",
    data(){
      return {
        recommendList: [{
        id: '001',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1609/80/8092254b7f5f016ea3.water.jpg_200x200_cd798d39.jpg',
        title: "宋豇豆角",
        desc: "登录客户端客服"
      },{
        id: '002',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1609/80/8092254b7f5f016ea3.water.jpg_200x200_cd798d39.jpg',
        title: "宋豇豆角",
        desc: "登录客户端客服"
      },{
        id: '003',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1609/80/8092254b7f5f016ea3.water.jpg_200x200_cd798d39.jpg',
        title: "宋豇豆角",
        desc: "登录客户端客服"
      }]
      }
    }
  }
  
</script>

<style scoped lang="stylus">
  .recommend-title
    margin-top: .2rem
    background: #ccc
    line-height: .6rem
    text-indent: .3rem
    border-radius: .02rem
  .item
    overflow: hidden
    display: flex
    height: 1.9rem
    .item-img
      width: 1.7rem
      height: 1.7rem
      padding: .1rem
    .item-info
      flex: 1
      padding: .1rem
      .item-title
        line-height: .54rem
        font-size: .32rem
      .item-desc
        line-height: .4rem
        color: #ccc
        padding: .1rem 0 
      .item-button
        background: #ff9300
        margin-top: .16rem
        line-height: .44rem
        padding: 0 .2rem
        color: #fff
        border-radius: .06rem


</style>