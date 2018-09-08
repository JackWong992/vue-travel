<template>
  <div>
    <div class="header">
    <router-link to="/">
      <span class="iconfont icon-fanhui"></span>      
    </router-link>
      城市推荐</div>
  </div>
</template>

<script>
  export default {
    name: 'CityHeader'
  }
</script>

<style scoped lang="stylus">
  @import "~@/assets/styles/varibles.styl"
  .header
    overflow: hidden
    position: relative 
    height: .86rem
    line-height: .86rem
    text-align: center
    background: $bgColor
    color: #fff
    font-size: .32rem
    .icon-fanhui
      position: absolute
      color: #fff
      left: 0
      top: 0
      width: .64rem
      text-align: center
      font-size: .4rem 
</style>