<template>
  <div>
    <div class="weekend-title">周末推荐</div>
    <ul>
      
      <li class="item border-bottom" v-for="item in list"
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
    props: {
      list: Array
    },
    data(){
      return {}
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
    padding-bottom: 37.09% 
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