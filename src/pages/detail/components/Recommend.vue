<template>
  <div>
    <div class="recommend-title border-bottom">
        <span class="iconfont icon-xiaoxi-"></span>去哪儿推荐</div>
    <div class="recommend-content border-bottom" 
    v-for="(item,index) in content" :key="index">
      <div class="recommend-desc">
        {{item.desc}}</div>
      <div class="recommend-pay">￥{{item.pay}}</div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'DeatailRecommend',
    data() {
      return {
        content: [
        {desc: "上海杜莎夫人蜡像成人票",pay: 170},
        {desc: "杜莎夫人蜡像馆+东方明珠",pay: 288},
        {desc: "杜莎夫人成人秋日茶饮套餐", pay: 199}]
      }
    },
  }
</script>

<style scoped lang="stylus">
  .recommend-title
    font-size: .32rem
    text-indent: .2rem
    padding: .15rem 0
  .recommend-content
    display: flex
    justify-content: space-between
    padding: .3rem  0  .3rem .3rem
    font-size: .24rem  
  .recommend-pay
    margin-right: .3rem
    height: .3rem
    line-height: .3rem
    border-radius: .06rem  
    background: #fd9a30  
    color: #fff
    text-align:center
    padding: .045rem
</style>